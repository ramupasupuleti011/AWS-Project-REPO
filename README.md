# Deploying a Production-Grade, Highly Available and Scalable 3-Tier Architecture on AWS

A hands-on AWS project demonstrating how a web application can be structured into presentation, application, and database tiers, with traffic distribution and redundancy across multiple Availability Zones.

**Repository:** [AWS-Project-REPO](https://github.com/ramupasupuleti011/AWS-Project-REPO)

## Project Overview

This project focuses on designing an AWS architecture for availability, scalability, network separation, and database resilience. The architecture diagram illustrates a user request flowing through DNS and edge/network entry services to load-balanced application components, with a database tier containing primary and standby database instances.

> **Implementation note:** This README describes the architecture shown in the supplied diagram. Confirm the actual AWS resources, configuration, and deployment steps in the repository before claiming that every component has been deployed or tested.

## Architecture

![AWS 3-Tier Highly Available and Scalable Architecture]

The diagram shows a multi-AZ design with these main layers:

1. **DNS and edge entry:** Amazon Route 53 is shown as the DNS entry point. The diagram also includes an edge/distribution service in front of the application.
2. **Presentation tier:** Frontend application instances are distributed across Availability Zones and use frontend technologies represented in the diagram, including React and NGINX.
3. **Application tier:** Backend application instances run in separate application components. Node.js is represented in the diagram.
4. **Database tier:** A MySQL database is shown with a primary database and a standby instance.
5. **Availability and traffic distribution:** Load-balancing components route incoming traffic to application instances across Availability Zones.
6. **Network and access boundaries:** The diagram depicts separate boundaries around the AWS environment, Availability Zones, and application/database components.

## Key Design Goals

- **High availability:** Spread application components across multiple Availability Zones to reduce dependence on a single zone.
- **Scalability:** Distribute requests across multiple application instances and allow capacity to be expanded as needed.
- **Tier separation:** Keep presentation, application, and database responsibilities logically separated.
- **Database resilience:** Include primary and standby database instances in the database tier.
- **Controlled access:** Use network boundaries and security controls to limit access between tiers.
- **Maintainability:** Organize the infrastructure so individual tiers can be monitored and updated independently.

These are architecture goals. Actual availability, scaling behavior, failover, and security depend on the resources and settings implemented in AWS.

## AWS Services and Technologies

The supplied diagram indicates or suggests the following components. Update this list to match the resources actually present in the repository.

| Component | Purpose |
|---|---|
| Amazon Route 53 | DNS routing to the application entry point |
| Edge/distribution service | Front-door delivery layer shown in the diagram |
| Load balancers | Distribute requests between application instances |
| Amazon VPC | Network boundary for the AWS workload |
| Multiple Availability Zones | Place application and database components in separate zones |
| Amazon EC2 | Compute instances for application tiers, as represented by the compute icons |
| React and NGINX | Frontend technologies represented in the diagram |
| Node.js | Backend application technology represented in the diagram |
| MySQL | Relational database engine represented in the diagram |
| Security groups / network controls | Restrict traffic between tiers |

## Request Flow

1. A user accesses the application through its DNS name.
2. DNS and the edge/entry layer direct the request toward the application.
3. A load balancer routes the request to an available frontend instance.
4. The frontend communicates with the backend application tier as required.
5. The backend tier accesses the database tier.
6. Application components in another Availability Zone provide redundancy, while database standby/failover behavior depends on the database configuration.

## Deployment and Validation

The exact deployment commands depend on the infrastructure code and scripts in this repository. Review the repository files before running commands.

Recommended validation checklist:

- [ ] Confirm the VPC and subnet layout across the intended Availability Zones.
- [ ] Confirm route tables, internet/NAT routing, and security group rules.
- [ ] Confirm target groups and health checks for each load balancer.
- [ ] Confirm frontend and backend instances are healthy and reachable through the intended entry point.
- [ ] Confirm the application can connect to the database without exposing the database publicly.
- [ ] Confirm database backup, replication, and failover configuration.
- [ ] Test application behavior when an instance becomes unhealthy.
- [ ] Test scaling behavior, if Auto Scaling is configured.
- [ ] Review CloudWatch metrics and logs, if monitoring is configured.
- [ ] Check AWS costs and remove resources after testing when they are no longer needed.

Do not claim successful failover, auto scaling, monitoring, or production readiness until those behaviors have been configured and tested.

## Security and Cost Considerations

- Follow least-privilege IAM permissions.
- Keep database resources in private subnets where supported by the implementation.
- Permit only the required ports between tiers.
- Avoid hardcoding AWS access keys or passwords in source code.
- Use managed secrets and encryption where appropriate.
- Enable backups and define a recovery approach before storing important data.
- Review resource sizes, load balancer usage, NAT Gateway costs, and database charges.
- Run `terraform destroy` only when appropriate and only after confirming that no required resources or data will be removed.

## Skills Demonstrated

This project can demonstrate practical understanding of:

- AWS networking and VPC design
- Multi-AZ architecture concepts
- Load balancing and health checks
- Three-tier application design
- Compute and database tier separation
- Security group and IAM fundamentals
- Availability, scalability, and resilience concepts
- Cloud architecture documentation and troubleshooting

Only list tools such as Terraform, CloudFormation, CI/CD, or monitoring in your skills/project claims if they are actually used in this repository.

## Repository

- **GitHub:** https://github.com/ramupasupuleti011/AWS-Project-REPO

## Author

**Ramu Pasupuleti**  
B.Tech, Electrical and Electronics Engineering  
Interested in AWS Cloud, DevOps, infrastructure automation, and cloud architecture.


