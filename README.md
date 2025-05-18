# AWS

## ✅ 1. **Compute Services**

---

### 🔹 Amazon EC2 (Elastic Compute Cloud)

- 📖 **Definition**: Virtual servers (instances) in the cloud, providing resizable compute capacity.
- ⚙️ **Usage**: Host traditional applications, websites, backend services, batch processing, and more.
- ✅ Highly flexible (various instance types), scalable (with Auto Scaling), secure (Security Groups), choice of OS, persistent storage (EBS).
- ⚠️ Customer manages OS, patching, and application software. Can be complex to configure optimally without experience.
- 🎯 Use Cases: Web hosting, application servers, databases (self-managed), HPC, machine learning model training.
- 📝 **Note**: Key pricing models: On-Demand, Reserved Instances, Spot Instances, Savings Plans.

---

### 🔹 AWS Lambda

- 📖 **Definition**: Serverless, event-driven compute service that runs your code in response to events without provisioning or managing servers.
- ⚙️ **Usage**: Execute code for backend APIs, data processing, automation tasks, and microservices.
- ✅ No server management, automatic scaling, pay only for compute time consumed (per millisecond), highly available.
- ⚠️ Limited execution time (max 15 mins), potential cold starts, stateless by default (requires external storage for state).
- 🎯 Use Cases: Image/video processing upon S3 upload, API backends with API Gateway, real-time data processing, scheduled tasks.
- 📝 **Note**: Supports various runtimes (Python, Node.js, Java, etc.) or custom runtimes.

---

### 🔹 AWS Elastic Beanstalk

- 📖 **Definition**: Platform as a Service (PaaS) for deploying and scaling web applications and services developed with common languages/platforms.
- ⚙️ **Usage**: Simplifies the deployment process; developers upload code, and Beanstalk handles capacity provisioning, load balancing, auto-scaling, and health monitoring.
- ✅ Easy to use, reduces management overhead, handles underlying infrastructure (EC2, S3, ELB, ASG), supports popular platforms (Java, .NET, PHP, Node.js, Python, Ruby, Go, Docker).
- ⚠️ Less granular control than managing individual services directly; abstraction layer can sometimes make complex troubleshooting harder.
- 🎯 Use Cases: Quickly deploying web applications, APIs, microservices, worker environments.
- 📝 **Note**: Uses AWS CloudFormation templates under the hood to provision resources.

---

### 🔹 AWS Batch

- 📖 **Definition**: Managed service for efficiently running hundreds of thousands of batch computing jobs on AWS.
- ⚙️ **Usage**: Dynamically provisions optimal compute resources (EC2 On-Demand or Spot) based on job volume and requirements.
- ✅ Managed compute environments and job queues, cost optimization with Spot Instances, no batch software to install/manage.
- ⚠️ Primarily for non-interactive, long-running batch workloads; not for real-time or interactive applications.
- 🎯 Use Cases: Large-scale data processing, financial modeling, scientific research, media rendering.
- 📝 **Note**: Integrates with Docker containers for packaging batch applications.

---

### 🔹 AWS Outposts

- 📖 **Definition**: Brings native AWS services, infrastructure, and operating models to virtually any data center, co-location space, or on-premises facility.
- ⚙️ **Usage**: Extends AWS to on-premises for low-latency requirements, local data processing, or data residency.
- ✅ Consistent hybrid experience (same APIs, tools, hardware as in AWS regions), fully managed by AWS.
- ⚠️ Requires physical space and power on-premises; AWS manages the hardware, but customer is responsible for the physical environment.
- 🎯 Use Cases: Workloads needing single-digit millisecond latency to on-premises systems, local data processing, data residency.
- 📝 **Note**: Supports select AWS services like EC2, EBS, S3, RDS, ECS, EKS.

---

### 🔹 AWS Wavelength

- 📖 **Definition**: Embeds AWS compute and storage services within telecommunications providers' 5G networks.
- ⚙️ **Usage**: Delivers ultra-low-latency applications to 5G mobile devices and end-users.
- ✅ Single-digit millisecond latencies for mobile edge applications, seamless extension of your VPC.
- ⚠️ Limited service availability (tied to specific 5G provider networks and locations), focused on edge compute for mobile.
- 🎯 Use Cases: AR/VR, game streaming, connected vehicles, real-time inference at the edge for mobile.
- 📝 **Note**: Resources are deployed to Wavelength Zones, which are infrastructure deployments within telco provider data centers at the edge of the 5G network.

---

### 🔹 AWS Local Zones

- 📖 **Definition**: An extension of an AWS Region that places AWS compute, storage, database, and other select services closer to large population, industry, and IT centers.
- ⚙️ **Usage**: Run latency-sensitive applications closer to end-users in specific geographic areas without needing to provision in a more distant AWS Region.
- ✅ Low-latency access for end-users in specific metros, seamless VPC extension, use familiar AWS APIs.
- ⚠️ Offers a subset of AWS services compared to a full Region; primarily for latency-sensitive parts of applications.
- 🎯 Use Cases: Media & entertainment content creation, real-time gaming, live video streaming, engineering simulations.
- 📝 **Note**: Helps address data residency or local data processing needs in areas without a full AWS Region.

---

## ✅ 2. **Storage Services**

---

### 🔹 Amazon S3 (Simple Storage Service)

- 📖 **Definition**: Scalable, durable, and secure object storage service for a wide variety of use cases.
- ⚙️ **Usage**: Store and retrieve any amount of data, at any time, from anywhere on the web.
- ✅ High durability (11 nines), high availability, various storage classes (cost/performance), versioning, replication (CRR/SRR), static website hosting, event notifications.
- ⚠️ Not suitable for operating systems or transactional databases (use EBS/RDS); eventually consistent for overwrites/deletes (strong consistency for new objects).
- 🎯 Use Cases: Backup and restore, data archiving, data lakes, static website hosting, application data.
- 📝 **Note**: Bucket names are globally unique. Objects are files, buckets are containers.

---

### 🔹 Amazon EBS (Elastic Block Store)

- 📖 **Definition**: Persistent block storage volumes (like virtual hard disks) for use with Amazon EC2 instances.
- ⚙️ **Usage**: Provides storage for the root device (OS) or additional storage for EC2 instances.
- ✅ Persistent (data survives instance stop/start), various volume types (SSD, HDD for different performance/cost), snapshots for backup (to S3), encryption.
- ⚠️ Tied to a specific Availability Zone (AZ) by default (snapshots are regional), performance depends on volume type and instance type.
- 🎯 Use Cases: EC2 instance boot volumes, databases on EC2, applications requiring block-level storage.
- 📝 **Note**: Snapshots are incremental and stored in S3, providing a cost-effective backup solution.

---

### 🔹 Amazon EFS (Elastic File System)

- 📖 **Definition**: Scalable, fully managed, elastic NFS file system for use with AWS Cloud services and on-premises resources.
- ⚙️ **Usage**: Provides shared file storage for multiple EC2 instances (and other services like ECS, EKS, Lambda) across multiple AZs within a region.
- ✅ Highly available and durable (data stored across multiple AZs), scales automatically, pay-for-use, supports NFSv4 protocol.
- ⚠️ Higher cost per GB than S3 or EBS for some use cases; performance can vary based on mode (General Purpose, Max I/O) and throughput settings.
- 🎯 Use Cases: Content management systems, web serving, shared code repositories, big data analytics requiring a file system interface.
- 📝 **Note**: Can be mounted by multiple EC2 instances simultaneously, ideal for shared access.

---

### 🔹 Amazon S3 Glacier & Glacier Deep Archive

- 📖 **Definition**: Secure, durable, and extremely low-cost cloud storage services for data archiving and long-term backup.
- ⚙️ **Usage**: Store data that is infrequently accessed and for which retrieval times of minutes to hours are acceptable.
- ✅ Extremely low storage costs, high durability, various retrieval options (Expedited, Standard, Bulk for Glacier).
- ⚠️ Not for frequently accessed data; retrieval times are not instant (Glacier: mins to hrs; Deep Archive: hrs). Retrieval costs can be significant if large amounts are retrieved.
- 🎯 Use Cases: Long-term data archives, regulatory compliance archives, digital media archives, disaster recovery backups.
- 📝 **Note**: S3 Glacier Deep Archive is the lowest-cost S3 storage class, designed for data accessed once or twice a year.

---

### 🔹 AWS Snowball Family (Snowball, Snowball Edge)

- 📖 **Definition**: Physical data transport solutions using secure appliances to transfer large amounts of data into and out of AWS.
- ⚙️ **Usage**: Overcome network limitations for large-scale data migrations or when network connectivity is poor. Snowball Edge also provides compute capabilities for edge locations.
- ✅ Secure (tamper-evident, encryption), cost-effective for petabyte-scale transfers, Snowball Edge offers local compute and storage.
- ⚠️ Physical shipping involved; not for continuous data transfer (use Direct Connect or S3 Transfer Acceleration for that).
- 🎯 Use Cases: Large data migrations (petabytes), data center decommissioning, disaster recovery, edge computing (Snowball Edge).
- 📝 **Note**: Choose based on data volume: Snowball for terabytes, Snowmobile (truck) for exabytes. Snowball Edge has compute options.

---

### 🔹 S3 Transfer Acceleration

- 📖 **Definition**: Enables fast, easy, and secure transfers of files over long distances between your client and an S3 bucket.
- ⚙️ **Usage**: Speeds up S3 uploads/downloads over the public internet by routing traffic through CloudFront's globally distributed edge locations.
- ✅ Faster transfers for geographically dispersed users, simple to enable (bucket-level setting), secure.
- ⚠️ Incurs additional cost; most beneficial for transfers over long distances or where internet routing is suboptimal.
- 🎯 Use Cases: Uploading large media files from distributed users, regular data transfers from remote offices to a central S3 bucket.
- 📝 **Note**: Uses CloudFront edge network but is specific to S3 transfers, unlike Global Accelerator which is for general application traffic.

---

## ✅ 3. **Networking & Content Delivery Services**

---

### 🔹 Amazon VPC (Virtual Private Cloud)

- 📖 **Definition**: A logically isolated section of the AWS Cloud where you can launch AWS resources in a virtual network that you define.
- ⚙️ **Usage**: Provides control over your virtual networking environment, including IP address range selection, subnets, route tables, and network gateways.
- ✅ Full control over network configuration, security via Security Groups and Network ACLs, enables private connectivity.
- ⚠️ Can be complex to set up correctly (CIDR blocks, routing, subnets); misconfiguration can lead to connectivity or security issues.
- 🎯 Use Cases: Hosting multi-tier applications, creating private networks, connecting to on-premises data centers.
- 📝 **Note**: Foundation of most AWS deployments, allowing you to build your own private network in the cloud.

---

### 🔹 Internet Gateway (IGW)

- 📖 **Definition**: A horizontally scaled, redundant, and highly available VPC component that allows communication between instances in your VPC and the internet.
- ⚙️ **Usage**: Enables instances with public IP addresses in public subnets to access the internet and be reached from the internet.
- ✅ Managed by AWS (no single point of failure), essential for internet-facing resources.
- ⚠️ Only one IGW can be attached to a VPC. Requires a route in the public subnet's route table (0.0.0.0/0 -> IGW).
- 🎯 Use Cases: Allowing web servers in a public subnet to serve traffic, enabling EC2 instances to download updates.
- 📝 **Note**: Does not provide NAT capabilities; for that, use NAT Gateway or NAT Instance.

---

### 🔹 NAT Gateway (Network Address Translation)

- 📖 **Definition**: A managed AWS service that enables instances in a private subnet to connect to the internet or other AWS services, but prevents the internet from initiating connections with those instances.
- ⚙️ **Usage**: Allows outbound internet access for private instances (e.g., for software updates) while keeping them secure from inbound connections.
- ✅ Managed by AWS (highly available, scalable), simpler than managing NAT Instances, automatically assigned an Elastic IP.
- ⚠️ Resides in a public subnet; incurs costs per hour and per GB processed.
- 🎯 Use Cases: Allowing backend servers in private subnets to download patches, access external APIs.
- 📝 **Note**: Preferred over self-managed NAT Instances due to better availability and less management overhead.

---

### 🔹 Elastic IP (EIP)

- 📖 **Definition**: A static, public IPv4 address designed for dynamic cloud computing, which you can allocate to your account and associate with an EC2 instance or network interface.
- ⚙️ **Usage**: Provides a persistent public IP address that can be remapped to mask instance or availability zone failures.
- ✅ Static IP that doesn't change if an instance is stopped/restarted, can be easily moved between instances.
- ⚠️ Charged if allocated but not associated with a running instance, or associated with a stopped instance, or associated with an ENI not attached to an instance. Limited number per account.
- 🎯 Use Cases: Hosting internet-facing services requiring a fixed IP, quickly remapping an IP to a healthy instance during failover.
- 📝 **Note**: Useful for services like NAT Gateways or customer-facing endpoints that need a stable public IP.

---

### 🔹 AWS PrivateLink

- 📖 **Definition**: Provides private connectivity between VPCs, AWS services, and your on-premises networks without exposing your traffic to the public internet.
- ⚙️ **Usage**: Access AWS services (S3, Kinesis, etc.) or your own services (Endpoint Services) as if they were in your VPC using Interface VPC Endpoints.
- ✅ Secure (traffic stays on AWS network), simplifies network architecture (no IGW, NAT, VPN needed for specific service access).
- ⚠️ Service-specific connectivity (not full network peering); endpoint services require an NLB.
- 🎯 Use Cases: Securely accessing S3 from a private subnet, private access to SaaS applications hosted on AWS.
- 📝 **Note**: Powers Interface VPC Endpoints. Gateway VPC Endpoints (for S3, DynamoDB) are a different mechanism but also provide private access.

---

### 🔹 Site-to-Site VPN

- 📖 **Definition**: Creates a secure, encrypted tunnel between your on-premises network/data center and your AWS VPC over the public internet.
- ⚙️ **Usage**: Connect your corporate network to your AWS environment.
- ✅ Secure (IPSec encryption), relatively quick to set up, cost-effective for moderate bandwidth needs.
- ⚠️ Relies on the public internet (performance can vary), bandwidth limited by internet connection.
- 🎯 Use Cases: Extending on-premises networks to AWS, hybrid cloud architectures.
- 📝 **Note**: Uses a Virtual Private Gateway (VGW) or Transit Gateway on AWS side and a Customer Gateway (CGW) on your side.

---

### 🔹 AWS Direct Connect (DX)

- 📖 **Definition**: Establishes a dedicated private network connection from your premises to AWS, bypassing the public internet.
- ⚙️ **Usage**: For consistent, high-bandwidth, low-latency private connectivity to AWS.
- ✅ Consistent network performance, potentially lower data transfer costs (outbound), higher bandwidth options (1 Gbps, 10 Gbps, 100 Gbps).
- ⚠️ Higher initial setup cost and longer lead time than VPN; requires a connection at an AWS Direct Connect location.
- 🎯 Use Cases: Hybrid workloads requiring high bandwidth, transferring large datasets, applications sensitive to network latency.
- 📝 **Note**: Often used with Site-to-Site VPN as a backup connection.

---

### 🔹 AWS Client VPN

- 📖 **Definition**: A managed client-based VPN service that enables users to securely connect to AWS or on-premises networks from anywhere using an OpenVPN-based client.
- ⚙️ **Usage**: Provides secure access for remote employees or users to resources within a VPC or on-premises network.
- ✅ Managed service, scalable, supports various authentication methods (AD, SAML, certificates).
- ⚠️ Per-user connection model; distinct from Site-to-Site VPN which connects entire networks.
- 🎯 Use Cases: Secure remote access for employees, connecting individual devices to AWS resources.
- 📝 **Note**: Allows users to connect from any location using an OpenVPN compatible client software.

---

### 🔹 Transit Gateway (TGW)

- 📖 **Definition**: A network hub that acts as a cloud router to connect multiple VPCs and on-premises networks.
- ⚙️ **Usage**: Simplifies network connectivity by replacing complex VPC peering meshes and providing a central point for routing.
- ✅ Transitive routing (VPCs connected to TGW can communicate with each other), scalable, simplifies network management for many VPCs.
- ⚠️ Incurs costs per attachment and per GB processed; can become a central point if not designed for HA.
- 🎯 Use Cases: Connecting hundreds or thousands of VPCs, simplifying hybrid connectivity, centralizing network services.
- 📝 **Note**: A significant improvement over complex VPC peering, especially for large-scale networks.

---

### 🔹 Amazon CloudFront

- 📖 **Definition**: A global Content Delivery Network (CDN) service that securely delivers data, videos, applications, and APIs to customers globally with low latency and high transfer speeds.
- ⚙️ **Usage**: Caches content (static and dynamic) at Edge Locations closer to end-users to reduce latency.
- ✅ Improved website/application performance, reduced latency, DDoS protection (integrates with Shield, WAF), scalable.
- ⚠️ Can be complex to configure for dynamic content or specific caching behaviors; cost depends on data transfer out and requests.
- 🎯 Use Cases: Accelerating static website delivery, video streaming, API acceleration, distributing software.
- 📝 **Note**: Integrates with S3, EC2, ELB, and Route 53 as origin servers.

---

### 🔹 Amazon Route 53

- 📖 **Definition**: A highly available and scalable cloud Domain Name System (DNS) web service.
- ⚙️ **Usage**: Translates human-readable domain names (e.g., www.example.com) into IP addresses; also offers domain registration and various routing policies.
- ✅ Highly available (100% uptime SLA), scalable, global network of DNS servers, advanced routing policies (latency, geolocation, failover, weighted), health checks.
- ⚠️ Costs are per hosted zone and per query (though often very low for typical usage).
- 🎯 Use Cases: Domain name registration, DNS resolution, traffic routing for applications, creating failover configurations.
- 📝 **Note**: Integrates with ELB, CloudFront, S3 static websites for routing traffic to AWS resources.

---

### 🔹 AWS Global Accelerator

- 📖 **Definition**: A networking service that improves the availability and performance of your applications with local or global users by directing traffic to optimal endpoints over the AWS global network.
- ⚙️ **Usage**: Provides static anycast IP addresses as a fixed entry point and optimizes the path from users to your application endpoints (ALB, NLB, EC2, EIP).
- ✅ Improved application performance (reduced latency, jitter), increased availability (failover across regions), static IP addresses.
- ⚠️ Not a CDN (doesn't cache content like CloudFront); incurs costs for the accelerator and data processed.
- 🎯 Use Cases: Global applications requiring low latency (gaming, VoIP), improving TCP/UDP application performance, providing stable entry points for applications.
- 📝 **Note**: Different from CloudFront: Global Accelerator optimizes the network path for TCP/UDP traffic and provides static IPs; CloudFront caches HTTP/S content at the edge.

---

## ✅ 4. **Databases**

---

### 🔹 Amazon RDS (Relational Database Service)

- 📖 **Definition**: A managed service for setting up, operating, and scaling relational databases in the cloud.
- ⚙️ **Usage**: Host common relational database engines without managing the underlying infrastructure.
- ✅ Managed (patching, backups, HA with Multi-AZ), scalable (compute & storage), supports various engines (MySQL, PostgreSQL, MariaDB, SQL Server, Oracle, Aurora), Read Replicas for read scaling.
- ⚠️ You don't have OS-level access; some advanced DB features might be restricted compared to self-managed.
- 🎯 Use Cases: Web and mobile application backends, enterprise applications requiring relational databases.
- 📝 **Note**: Multi-AZ for high availability (synchronous replication), Read Replicas for read scalability (asynchronous replication).

---

### 🔹 Amazon Aurora

- 📖 **Definition**: A MySQL and PostgreSQL-compatible relational database built for the cloud, offering high performance, availability, and scalability. It's an engine option within RDS.
- ⚙️ **Usage**: For demanding relational database workloads requiring better performance and reliability than standard MySQL/PostgreSQL.
- ✅ High performance (up to 5x MySQL, 3x PostgreSQL), auto-scaling storage (up to 128TB), fault-tolerant (6 copies of data across 3 AZs), Aurora Serverless option.
- ⚠️ Generally more expensive per instance-hour than standard RDS engines, but can be more cost-effective due to performance and features.
- 🎯 Use Cases: High-throughput OLTP applications, enterprise applications, SaaS applications.
- 📝 **Note**: Offers features like Global Database for multi-region replication and fast disaster recovery.

---

### 🔹 Amazon DynamoDB

- 📖 **Definition**: A fully managed, serverless, key-value and document NoSQL database delivering single-digit millisecond performance at any scale.
- ⚙️ **Usage**: For applications requiring high scalability, low latency, and flexible data models.
- ✅ Highly scalable (horizontal scaling), serverless (no servers to manage), fast and consistent performance, Global Tables for multi-region, DAX for in-memory caching.
- ⚠️ Not suitable for complex relational joins or ACID transactions across multiple items in the same way as SQL DBs; query patterns need to be considered during design.
- 🎯 Use Cases: Mobile apps, gaming, IoT, ad tech, e-commerce platforms, any application needing high scale and low latency.
- 📝 **Note**: Two capacity modes: On-Demand (pay-per-request) and Provisioned (specify read/write capacity).

---

### 🔹 Amazon ElastiCache

- 📖 **Definition**: A managed in-memory caching service that improves application performance by retrieving data from fast, managed, in-memory caches instead of slower disk-based databases.
- ⚙️ **Usage**: Cache frequently accessed data to reduce database load and improve application response times.
- ✅ Managed service, supports two engines (Memcached: simpler, Redis: richer features), improves read latency.
- ⚠️ Adds another layer to manage/consider in architecture; can increase cost if not used effectively.
- 🎯 Use Cases: Reducing database load for read-heavy applications, session management, real-time leaderboards (Redis).
- 📝 **Note**: Redis offers more features like persistence, pub/sub, data structures, and Multi-AZ. Memcached is simpler for pure caching.

---

### 🔹 Amazon DocumentDB (with MongoDB compatibility)

- 📖 **Definition**: A fast, scalable, highly available, and fully managed document database service that supports MongoDB workloads.
- ⚙️ **Usage**: For applications that use MongoDB and want a managed database service on AWS.
- ✅ MongoDB-compatible API, managed (patching, backups), scalable, highly available.
- ⚠️ Not all MongoDB features/versions are supported; it's "compatible" not a drop-in MongoDB replacement in all cases.
- 🎯 Use Cases: Migrating MongoDB applications to AWS, content management, mobile application backends requiring a document store.
- 📝 **Note**: Different from DynamoDB (which also supports document models) primarily in its MongoDB API compatibility and query language.

---

### 🔹 Amazon Neptune

- 📖 **Definition**: A fast, reliable, fully managed graph database service for building and running applications that work with highly connected datasets.
- ⚙️ **Usage**: Model and query relationships between data points.
- ✅ Optimized for graph queries (traversing relationships), supports open graph APIs (Gremlin, SPARQL), highly available and durable.
- ⚠️ Niche database type; requires understanding graph data models and query languages.
- 🎯 Use Cases: Social networks, recommendation engines, fraud detection, knowledge graphs.
- 📝 **Note**: Ideal when the relationships between data are as important as the data itself.

---

### 🔹 Amazon Timestream

- 📖 **Definition**: A fast, scalable, and serverless time series database service for IoT and operational applications.
- ⚙️ **Usage**: Store and analyze trillions of time-stamped events per day.
- ✅ Optimized for time series data (ingestion, storage, query), serverless, built-in analytics functions for time series.
- ⚠️ Specific to time-series data; not a general-purpose database.
- 🎯 Use Cases: IoT sensor data, application monitoring metrics, industrial telemetry data.
- 📝 **Note**: Automatically tiers data between an in-memory store (fast access to recent data) and a magnetic store (cost-effective long-term storage).

---

### 🔹 Amazon Quantum Ledger Database (QLDB)

- 📖 **Definition**: A fully managed ledger database providing a transparent, immutable, and cryptographically verifiable transaction log owned by a central trusted authority.
- ⚙️ **Usage**: Maintain a complete and verifiable history of all changes to application data.
- ✅ Immutable (append-only), cryptographically verifiable data integrity, serverless, SQL-like query language (PartiQL).
- ⚠️ Centralized ledger (unlike decentralized blockchains); not for scenarios requiring multi-party consensus without a central authority.
- 🎯 Use Cases: Systems of record, audit trails, tracking item lineage (e.g., supply chain), financial transaction history.
- 📝 **Note**: Different from Managed Blockchain; QLDB is a centralized database with ledger capabilities.

---

## ✅ 5. **Management & Governance Tools**

---

### 🔹 AWS CloudFormation

- 📖 **Definition**: An Infrastructure as Code (IaC) service that allows you to model, provision, and manage AWS and third-party resources using template files (JSON or YAML).
- ⚙️ **Usage**: Automate the setup and management of your AWS infrastructure in a repeatable and consistent manner.
- ✅ Automated provisioning, repeatable deployments, change management (updates/deletions via "stacks"), version control for infrastructure.
- ⚠️ Steeper learning curve for complex templates; drift detection and management can be challenging.
- 🎯 Use Cases: Deploying multi-tier applications, creating standardized environments (dev, test, prod), disaster recovery setup.
- 📝 **Note**: Creates "stacks" of resources. Changes are managed by updating the stack.

---

### 🔹 AWS Cloud Development Kit (CDK)

- 📖 **Definition**: An open-source software development framework to define your cloud application resources using familiar programming languages (e.g., TypeScript, Python, Java).
- ⚙️ **Usage**: Define cloud infrastructure in code with higher-level constructs, which then synthesizes into CloudFormation templates.
- ✅ Use familiar programming languages, leverage software engineering practices (loops, conditions, objects), higher-level abstractions ("Constructs").
- ⚠️ Requires programming knowledge; adds an abstraction layer over CloudFormation.
- 🎯 Use Cases: Teams comfortable with programming wanting to define infrastructure, complex conditional logic for resource creation.
- 📝 **Note**: Compiles down to CloudFormation templates for deployment.

---

### 🔹 AWS Systems Manager (SSM)

- 📖 **Definition**: A unified operational hub providing visibility and control of your infrastructure on AWS and on-premises.
- ⚙️ **Usage**: Automate operational tasks like patching, configuration management, and secure remote access.
- ✅ Centralized management, automation (Run Command, Patch Manager, State Manager), secure access (Session Manager), parameter/secret storage (Parameter Store).
- ⚠️ Requires SSM Agent on managed instances; some features have costs or different tiers.
- 🎯 Use Cases: Patching fleets of EC2 instances, running ad-hoc commands, secure shell access without opening SSH ports, managing configuration state.
- 📝 **Note**: Parameter Store is a key feature for storing configuration data and secrets (can be free or paid for advanced).

---

### 🔹 AWS CloudWatch

- 📖 **Definition**: A monitoring and observability service for AWS resources and applications running on AWS.
- ⚙️ **Usage**: Collects and tracks metrics, collects and monitors log files, sets alarms, and automatically reacts to changes in your AWS resources.
- ✅ Comprehensive monitoring (Metrics, Logs, Alarms, Dashboards, Events/EventBridge), integrates with most AWS services, custom metrics.
- ⚠️ Can become costly with high-resolution custom metrics or large log volumes if not managed.
- 🎯 Use Cases: Monitoring EC2 CPU utilization, tracking Lambda errors, creating dashboards for application health, alerting on critical thresholds.
- 📝 **Note**: CloudWatch Metrics, Logs, Alarms, and EventBridge (formerly CloudWatch Events) are core components.

