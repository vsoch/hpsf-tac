### 1. Name of Project

**Flux Framework** (encompassing  all project repositories under the `flux-framework` GitHub organization such as `flux-core`, `flux-sched`, `flux-security`, `flux-accounting`, `flux-operator`, `flux-python`, `flux-restful-api`, and `flux-sched-py`.

### 2. Project Description

Flux Framework is a next-generation workload manager developed at Lawrence Livermore National Laboratory and deployed on the NNSA exascale system El Capitan along with several other Top 500 systems. Flux’s hierarchical scheduling architecture allows for nested instances that can manage resources at different levels of a system, from whole clusters down to individual cores. Its graph-based resource model provides rich, flexible expression and fine-grained control over diverse resources, making it uniquely suited for workloads with complex, heterogeneous requirements. Flux enables workflow components with different resource needs to coexist efficiently, addressing limitations in both traditional HPC schedulers and container orchestrators. Flux is called a "framework" because it is a suite of projects that assemble together to create the workload manager that we know as Flux. It is distinct from other workload managers due to its hierarchical scheduling, flexible resource model, and service- and event- driven architecture and oriented to serve emerging, dynamic and heteregenous workloads that coupled simulation with AI/ML demand. The Flux Framework consists of a modular ecosystem. We aim for Flux to join the High Performance Software Foundation (HPSF) to support the project continued growth. We highlight the following projects:

*   **flux-core:** The backbone of the framework. It provides the messaging overlay, module loading system, hierarchical tree management, and standardized interfaces (based on RFCs) for building HPC workload managers.
*   **flux-sched:** The graph-based scheduler module. It utilizes a directed graph model to represent resources, allowing it to schedule complex, heterogeneous hardware topologies with high throughput and devices like GPUs.
*   **flux-security:** The security infrastructure library and small setuid helper `imp`. It implements authentication and message integrity mechanisms to validate user credentials and requests, ensuring secure privilege separation and safe execution in multi-user environments.
*   **flux-accounting:** The accounting service providing banks, hierarchical shares and fair-share support for flux as well as long-term storage of events and usage.
*   **flux-operator:** A Kubernetes Operator that bridges HPC and Cloud Native. It automates the deployment of "MiniClusters"—fully functional Flux instances running as pods within Kubernetes. This enables seamless execution of MPI and HPC workloads inside Kubernetes without sacrificing the performance of a specialized batch scheduler.
*   **flux-python** & **flux-sched-py**: Comprehensive Python bindings for the core and scheduler, allowing users to write custom scheduling policies (e.g., AI-driven scheduling) in Python.
*  **flux-restful-api**: A web service that exposes Flux functionality over HTTP. This allows external systems (Web UIs, Workflow Engines, CI/CD pipelines) to submit jobs, query status, and inspect system state using standard REST patterns and JSON, removing the requirement for a local shell.
*  **fluence**: Custom scheduler plugin for Kubernetes that enables gang scheduling and more fine-grained topology specification for Job and related abstractions.
*  **dyad**: A module that provides an abstraction of shared storage over local storage resources, enabling orchestration of jobs that produce and consume data, acceleration of I/O-bound workloads, and optimized job scheduling with respect to data locality and dependencies.
*  **flux-coral2**: A project that provides specialized plugins and services tailored for the DOE CORAL-2 systems. These components enable Flux to manage and interact with specific system resources and services on those large-scale HPC platforms.
*  **PerfFlowAspect**: An Aspect Oriented Programming (AOP)-based tool to analyze cross-cutting performance concerns of composite science workflows. 
*  **flux-power-monitor**: Flux power monitoring and management modules.

We have chosen these projects to highlight that are most relevant to core Flux functionality ([flux-core](https://github.com/flux-framework/flux-core) and [flux-sched](https://github.com/flux-framework/flux-sched)) along with those that are or will be increasingly relevant to the AI/ML, cloud, or workflows communities (the remainder).

**Key Features:**

*   **Hierarchical Scaling:** Breaks the monolithic bottleneck by distributing scheduling decisions.
*   **Modern Accessibility:** Language SDKs (Python, Go, C/C++, Rust, RESTFul API) Enable the creation of tools that cross environments, including web-based portals, dashboards, and automated remote submission systems without custom socket programming.
*   **Graph-Based Scheduling:** Models complex hardware topologies natively.
*   **Converged Computing:** Runs natively on both bare metal and Kubernetes, cloud and HPC.
*   **Programmability:** The entire stack—from web API to scheduling algorithms—is accessible via modern languages (Python, Go, HTTP), making it the ideal testbed for systems research.
*   **Robust Security**: Enforces strict privilege separation, cryptographic message integrity, and distributed authentication (e.g., munge), ensuring safe, multi-user resource sharing across diverse environments.
*   **Data Intensive**: Projects are well-suited for data-intensive workflows involving AI/ML, inventory tracking, and integration of specialized storage.
*   **Performance**: Power-aware scheduling and monitoring capabilities.

Flux can be deployed as the system workload manager and scheduler, but also is flexible to be deployed under other workload managers. This deployment strategy is a site choice. Within the GitHub organization [flux-framework](https://github.com/flux-framework) and the associated [converged-computing](https://github.com/converged-computing) there are deployment methods that include Docker containers, Docker Compose, virtual machines with Terraform, Kubernetes, and SystemD units. The project has a Tutorials repository for lab-driven tutorial setup and content, and a suite of YouTube video Tutorials and talks.

### 3. Statement on Alignment with High Performance Software Foundation's Mission

Flux is a mature, open-source technology designed to solve the scalability and portability challenges of modern computing. The project aligns with the HPSF mission to "foster collaboration and stewardship of open source software projects that fuel innovation" in the following ways:

**3.1 Solving the Scalability Gap**
Flux addresses the "resource management gap" where static batch schedulers cannot keep up with dynamic, cloud-like, and ensemble workflows. By bringing Flux into HPSF, the foundation supports a critical architectural shift necessary for the post-Exascale era.

**3.2 Modernizing HPC Access**
Historical HPC tools are often isolated silos accessible only via SSH. By including **flux-restful-api**, **flux-python**, and **flux-sched-py** this project aligns with the goal of making HPC accessible to a broader audience. It allows developers to build modern web interfaces and automated pipelines on top of HPC infrastructure, modernizing the user experience.

**3.3 Bridging HPC and Cloud (Converged Computing)**
With the inclusion of the **flux-operator**, this project directly supports the industry's move toward Cloud Native HPC. Flux provides a unique solution that allows HPSF to govern a tool that is as relevant in the cloud as it is on bare metal.

**3.4 Enabling Innovation via Custom Scheduling**
By including **flux-sched-py**, Flux aligns with HPSF's mission to "fuel innovation." It allows data scientists to prototype novel scheduling algorithms (such as Reinforcement Learning schedulers) in Python, drastically lowering the barrier to entry for systems research. The fluence and Flux Operator projects extend the scheduling capabilities of Flux to Kubernetes.

**3.5 Modular and Composable Design**
Flux is composed of loosely coupled modules. Core projects, API services, and plugins that can be developed within are independent. This modularity empowers researchers to swap components without forking the entire code base.

**3.6 Open Standards and Governance**
Flux is built on a "spec-first" philosophy. Protocols are defined in RFCs (Request for Comments) before implementation. This rigorous adherence to open standards fosters a healthy ecosystem where external tools can easily interface with the resource manager.

### 4. Project Website

[flux-framework.org](http://flux-framework.org)

### 5. Open Source License

*   **LGPL-3.0** (flux-core, flux-python, flux-sched, flux-security, dyad, PerfFlowAspect, flux-power-monitor)
*   **MIT** (flux-operator, flux-sched-py, flux-restful-api)
*   **Apache 2.0** (fluence)

[License File (flux-core)](https://github.com/flux-framework/flux-core/blob/master/LICENSE)
[License File (flux-sched)](https://github.com/flux-framework/flux-sched/blob/master/LICENSE)
[License File (flux-security)](https://github.com/flux-framework/flux-security/blob/master/LICENSE)
[License File (flux-operator)](https://github.com/flux-framework/flux-operator/blob/master/LICENSE)
[License File (flux-python)](https://github.com/flux-framework/flux-python/blob/master/LICENSE)
[License File (flux-sched-py)](https://github.com/converged-computing/flux-sched-py/blob/main/LICENSE)
[License File (flux-restful-api)](https://github.com/flux-framework/flux-restful-api/blob/master/LICENSE)
[License File (fluence)](https://github.com/flux-framework/flux-k8s/blob/master/LICENSE)
[License File (dyad)](https://github.com/flux-framework/dyad/blob/main/LICENSE)
[License File (flux-coral2)](https://github.com/flux-framework/flux-coral2/blob/master/LICENSE)
[License File (PerfFlowAspect](https://github.com/flux-framework/PerfFlowAspect/blob/main/LICENSE)
[License File (flux-power-monitor](https://github.com/flux-framework/flux-power-monitor/blob/monitor/LICENSE)

### 6. Code of Conduct

The Flux Framework organization includes all projects under a common [Code of Conduct](https://flux-framework.readthedocs.io/projects/flux-rfc/en/latest/spec_47.html). 

### 7. Governance Practices

The Flux Framework project describes roles, responsibilities, and decision-making mechanisms in a common [Flux Framework Project Governance](https://flux-framework.readthedocs.io/projects/flux-rfc/en/latest/spec_48.html) document.

### 8. Two Sponsors from the High Performance Software Foundation's Technical Advisory Committee

1.  *Xavier Delaruelle* ([@xdelaruelle](https://github.com/xdelaruelle))
2.  *Axel Huebl* ([@ax3l](https://github.com/ax3l))

### 9. What is the project's solution for source control?

All core project source code is maintained in GitHub repositories within the [Flux Framework Organization](https://github.com/flux-framework).

### 10. What is the project's solution for issue tracking?

Issues are tracked individually in the GitHub repositories for each component (e.g., `flux-core/issues`, `flux-restful-api/issues`). Discussions and design proposals are handled via GitHub Discussions and the Flux Discussion List at `flux-discuss@lists.llnl.gov`.

### 11. Please list all external dependencies and their license

<details>
<summary> Click here for the dependencies for each component project </summary>

## flux-core Dependencies

| Dependency | License |
| :--- | :--- |
| **ZeroMQ (libzmq)** | LGPL-3.0+ |
| **czmq** | MPL-2.0 |
| **hwloc** | BSD-3-Clause |
| **Lua** (5.1+) | MIT |
| **Jansson** | MIT |
| **libev** | BSD-2-Clause / GPL-2.0+ |
| **LZ4** | BSD-2-Clause |
| **SQLite** | Public Domain |
| **YAML-CPP** | MIT |
| **Boost** (Graph Library) | Boost Software License |
| **munge** (Optional) | GPL-3.0 |

## flux-sched Dependencies

| Dependency | License |
| :--- | :--- |
| **Boost** (Graph Library >= 1.66) | Boost Software License |
| **flux-core** | LGPL-3.0 |
| **hwloc** (>= 1.11.1) | BSD-3-Clause |
| **jansson** (>= 2.10) | MIT |
| **jsonschema** (Python module >= 2.3.0) | MIT |
| **libedit** | BSD-3-Clause |
| **libuuid** | BSD-3-Clause |
| **Python** (3.6+) | PSF License |
| **PyYAML** (Python module >= 3.10) | MIT |
| **yaml-cpp** | MIT |

### flux-security Dependencies

| Dependency | License |
| :--- | :--- |
| **libsodium** | ISC |
| **jansson** | MIT |
| **libuuid** (util-linux) | BSD-3-Clause |
| **munge** | GPL-3.0 |
| **Linux-PAM** | BSD-3-Clause / GPL |
| **pam_wrapper** | GPL-3.0 |
| **Autotools** (Autoconf, Automake, Libtool) | GPL-3.0 |
| **pkg-config** | GPL-2.0 |

### flux-operator Dependencies

**Direct Dependencies**

| Dependency | License |
| :--- | :--- |
| **github.com/go-logr/logr** | Apache-2.0 |
| **github.com/google/uuid** | BSD-3-Clause |
| **github.com/mitchellh/hashstructure/v2** | MIT |
| **k8s.io/api** | Apache-2.0 |
| **k8s.io/apimachinery** | Apache-2.0 |
| **k8s.io/client-go** | Apache-2.0 |
| **k8s.io/klog/v2** | Apache-2.0 |
| **k8s.io/kube-openapi** | Apache-2.0 |
| **sigs.k8s.io/controller-runtime** | Apache-2.0 |
| **sigs.k8s.io/yaml** | MIT |

### flux-restful-api Dependencies

| Dependency | License |
| :--- | :--- |
| **aiofiles** | Apache-2.0 |
| **alembic** | MIT |
| **fastapi** | MIT |
| **httpx** | BSD-3-Clause |
| **jinja2** | BSD-3-Clause |
| **Markdown** | BSD-3-Clause |
| **passlib[bcrypt]** | BSD-3-Clause |
| **pyaml** | MIT |
| **pydantic** | MIT |
| **pydantic-settings** | MIT |
| **pytest** | MIT |
| **python-dotenv** | BSD-3-Clause |
| **python-jose[cryptography]** | MIT |
| **python-multipart** | Apache-2.0 |
| **requests** | Apache-2.0 |
| **sqlalchemy** | MIT |
| **uvicorn** | BSD-3-Clause |

### flux-python Dependencies

| Dependency | License |
| :--- | :--- |
| **cffi** | MIT |
| **flux-core** | LGPL-3.0 |
| **pyyaml** | MIT |

### flux-sched-py Dependencies

| Dependency | License |
| :--- | :--- |
| **cython** | Apache-2.0 |
| **flux-sched** | GPL-3.0 |

### fluence Dependencies

| Dependency | License |
| :--- | :--- |
| **github.com/flux-framework/fluxion-go** | LGPL-3.0 |
| **github.com/stretchr/testify** | MIT |
| **google.golang.org/grpc** | Apache-2.0 |
| **google.golang.org/protobuf** | BSD-3-Clause |
| **gopkg.in/yaml.v2** | Apache-2.0 |
| **k8s.io/api** | Apache-2.0 |
| **k8s.io/apimachinery** | Apache-2.0 |
| **k8s.io/client-go** | Apache-2.0 |
| **k8s.io/klog/v2** | Apache-2.0 |
| **k8s.io/kubectl** | Apache-2.0 |

### dyad Dependencies

| Dependency | License |
| :--- | :--- |
| **jansson** | MIT |
| **MURMUR3** | in the public domain |
| **LIBB64**  |  Creative Commons Public Domain License |
| ** ucx** | BSD3 |
| **mochi-margo** | https://github.com/mochi-hpc/mochi-margo/blob/main/COPYRIGHT |
| **Boost** (multi_index) | Boost Software License |

### flux-coral2 Dependencies 

| Dependency | License |
| :--- | :--- |
| **jansson** | MIT |
| **libsodium** | ISC License |
| **libflux-core** | LGPL-3.0 (Project License) |
| **libpals** | GNU General Public License (GPL) v3.0 or later |
| **libcxi** | BSD-2-Clause |
| **Python** | Python Software Foundation License (PSF) |
| **Python Module: `kubernetes`** | Apache License 2.0 |
| **Python Module: `pylint`** | GPL-2.0-or-later |
| **Python Module: `sphinx`** | BSD License |
| **Python Module: `docutils`** | BSD, GPL, Public Domain (Multiple) |
| **libdl** | System Library License |

### PerfFlowAspect Dependencies

| Dependency | Version |
| :--- | :--- |
| **clang** | == 20.0 |
| **LLVM Development Files** | == 20.0 |
| **Jansson Development Files** | >= 2.6 |
| **OpenSSL Development Files** | >= 1.0.2 |
| **CMake** | >= 3.10 |
| **Flex Lexical Analyzer** | == 2.6.1 |
| **Bison Parser Generator** | == 3.0.4 |
| **Make Build Utility** | >= 3.82 |
| (Optional) **CUDA Toolkit** | >= 12.8 |

### flux-power-monitor Dependencies

| Dependency | Version |
| :--- | :--- |
| **Autoconf** | >= 2.69 |
| **C Compiler** | C99 support (Implicit) |
| **Libtool** | N/A |
| **pkg-config** | N/A |
| **Variorum Library** | Must be provided via `--with-variorum` |
| **libczmq** | N/A |
| **flux-core** | N/A |
| **libpthread** | N/A |
| **Pthreads Support** | N/A |
| **Jansson Library** | >= 2.7 |

</details>

### 12. Please describe your release methodology and mechanics

Flux utilizes Semantic Versioning.

*   **Releases:** Tagged releases are created on GitHub for all components.
*   **Distribution:**
    *   **HPC:** Source tarballs and Spack packages (`spack install flux-core`) are the primary method for bare-metal HPC.
    *   **Python/Web:** `flux-restful-api` is distributed as a Python package and a Container image.
    *   **Cloud/K8s:** The `flux-operator` and `fluence` projects are distributed via container images on GitHub Container Registry (ghcr.io) and Helm Charts.
*   **Cadence:** The core Flux projects follow a monthly release cadence matched to [TOSS](https://hpc.llnl.gov/software/toss-tri-lab-operating-system-stack) releases. For non-core projects (e.g., the Flux Operator) regular releases are cut as features mature. For all Flux projects, integration testing is performed for all changes and release candidates.

### 13. Please describe Software Quality efforts (CI, security, auditing)

*   **CI/CD:** GitHub Actions are used for all repos.
    *   *Core/Python:* Runs unit tests, `sharness` integration tests, and API tests.
    *   *REST API:* Runs Python test suites against a mock Flux instance and live integration tests.
    *   *Operator:* Runs End-to-End (E2E) tests against Kind/Minikube.
*   **Coverage:** Code coverage is tracked via Codecov.
*   **Static Analysis:** The core projects utilizes "merge on passing," LGTM and Coverity Scan.
*   **Security:** `flux-security` handles privilege separation on bare metal. The REST API relies on the underlying system auth or can be configured behind authentication proxies for web security.

### 14. Please list the project's leadership team

We differentiate between organization-level leadership with administration rights and tie-breaking control over the organization as a whole, the administrators, and project/repo-level leadership. This list represents the overall maintainers, with the projects they maintain and admin-status if applicable marked to the side.

**Project Leaders / Core Maintainers:**
*   **James Corbett** (LLNL) - Core, Sched, Flux CORAL-2
*   **Jim Garlick** (LLNL) - Administrator, Core 
*   **Mark Grondona** (LLNL) - Administrator, Core
*   **Dan Milroy** (LLNL) - Sched, Fluence
*   **Chris Moussa** (LLNL) - flux-accounting
*   **Tom Scogland** (LLNL) - Administrator, Core, Sched
*   **Vanessa Sochat** (LLNL) - Flux Operator, Flux Python, Flux Sched Py, Flux RESTful API, Fluence
*   **Jae-Seung Yeom** (LLNL) - dyad
*   **Tapasya Patki** (LLNL) - flux-power-monitor, PerfFlowAspect

### 15. Please list the project members with access to commit to the mainline of the project
Commit access is granted to the Maintainers of the respective repositories. Key committers include:

*   `chu11` (Albert Chu)
*   `jameshcorbett` (James Corbett)
*   `garlick` (Jim Garlick)
*   `grondo` (Mark Grondona)
*   `milroy` (Dan Milroy)
*   `trws` (Tom Scogland)
*   `vsoch` (Vanessa Sochat)
*   `JaeseungYeom` (Jae-Seung Yeom)
*   `tpatki` (Tapasya Patki)

### 16. Please describe the project's decision-making process

Flux uses a "lazy consensus" model for most changes.

*   **RFC Process:** Major architectural changes, protocol definitions, and API modifications must go through the [Flux RFC](https://flux-framework.readthedocs.io/projects/flux-rfc/en/latest/spec_1.html) process.
*   **Pull Requests:** All code changes require review by at least one other maintainer.
*   **Governance:** The maintainers resolves conflicts that cannot be settled by consensus in their projects, and administrators serve that role at the organization level.

### 17. What is the maturity level of your project?

[Established](https://github.com/hpsfoundation/tac?tab=readme-ov-file#established)

### 18. Please list the project's official communication channels

*   **Website:** [flux-framework.org](http://flux-framework.org)
*   **Mailing List:** [flux-framework List](mailto:flux-discuss@lists.llnl.gov)
*   **Slack:** [llnl-performance.slack.com](https://llnl-performance.slack.com)
*   **GitHub Discussions:** [flux-core Discussions](https://github.com/flux-framework/flux-core/discussions)

### 19. Please list the project's social media accounts

*   **Twitter/X:** [@FluxFramework](https://x.com/FluxFramework)

### 20. Please describe any existing financial sponsorships

*   Primary development is funded by the **U.S. Department of Energy (DOE)** and the **National Nuclear Security Administration (NNSA)**, previously under the Exascale Computing Project (ECP) and currently under the Advanced Simulation and Computing (ASC) program at LLNL.

### 21. Please describe the project's infrastructure needs or requests

**Needs:**
*   None immediate.

**Requests:**
*   Access to diverse hardware CI runners (specifically ARM64 and PowerPC as well as varied GPUs).
*   Cloud credits for large-scale integration testing.
