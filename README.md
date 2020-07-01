# SCARV: a side-channel hardened RISC-V platform

<!--- -------------------------------------------------------------------- --->

*Acting as a component part of the wider
[SCARV](https://www.scarv.org)
project,
the 
[RISC-V](https://riscv.org)
compatible SCARV micro-controller 
(comprising a processor core and SoC) 
is the eponymous, capstone output, 
e.g., representing a demonstrator for the
[XCrypto](https://github.com/scarv/xcrypto)
ISE.*

<!--- -------------------------------------------------------------------- --->

## Overview

In various ways,
[RISC-V](https://riscv.org)
is acting as a catalyst for research in computer architecture, while
also remaining a practical, industrially relevant option for concrete
products.
A central theme is that the open
[ISA](https://en.wikipedia.org/wiki/Instruction_set_architecture)
specifically has naturally led to a large number of associated,
[open-source](https://en.wikipedia.org/wiki/Open-source_hardware)
implementations.  This, in turn, allows direct use or refinement of
such implementations in order to fit or react to specific requirements
of a given use-case, market, or domain;
[documented](https://riscv.org/risc-v-cores)
implementations reflect this fact via their diversity, *and* maturity.

One such domain is that of security, where openness has the auxiliary
benefit of transparency: because many implementations of RISC-V are
available under
[open-source](https://en.wikipedia.org/wiki/Open-source_hardware)
licenses, they allow forms of security evaluation or verification that
would be impossible with proprietary alternatives.  This is a *massive*
advantage where trust is important, as evidenced by the use of RISC-V
as a basis for projects such as
[OpenTitan](https://opentitan.org).

The SCARV project has a *specific* remit, specifically focusing on the
support of
[cryptography](https://en.wikipedia.org/wiki/Cryptography)
as an enabling technology within more general solutions for challenges
related to (cyber-)security.  Representing the capstone output of said
project, the SCARV
[micro-controller](https://en.wikipedia.org/wiki/Microcontroller)
aims to support
efficient (e.g., low-latency, and low-footprint),
secure    (e.g., wrt. implementation attacks)
execution of software-based cryptographic workloads.  Of course, it is
one instance within a large design space: this means it will not be a
suitable choice for *every* use-case.  Even then, however, it acts as
an effective reference and demonstrator platform, for other components
of the overarching project (e.g., the
[XCrypto](https://github.com/scarv/xcrypto)
ISE).

<!--- -------------------------------------------------------------------- --->

## Organisation

```
├── bin                     - scripts (e.g., environment configuration)
├── build                   - working directory for build
├── doc                     - documentation
│   └── tex                   - LaTeX content
└── extern                  - external resources (e.g., submodules)
    ├── scarv-cpu             - submodule: scarv/scarv-cpu
    ├── scarv-soc             - submodule: scarv/scarv-soc
    ├── texmf                 - submodule: scarv/texmf
    └── wiki                  - submodule: scarv/scarv.wiki
```

*Originally* this was a 
[monorepo](https://en.wikipedia.org/wiki/Monorepo)
that housed *all* resources in one place, but, to make them easier to 
manage, it *now* acts as a container where each resource is housed in 
dedicated submodule.  Specifically, these include:

- [`scarv/scarv-cpu`](https://github.com/scarv/scarv-cpu)
  houses the
  processor core
  implementation;
  it includes a 5-stage, single issue, in-order 
  [pipeline](https://en.wikipedia.org/wiki/Pipeline_(computing)), 
  and implements the RISC-V 32-bit integer base architecture (i.e.,
  RV32I) *plus*

  - the     standard
    Compressed (C)
    and 
    Multiply   (M)
    extensions,
    and
  - the non-standard
    [XCrypto](https://github.com/scarv/xcrypto)
    extension.

- [`scarv/scarv-soc`](https://github.com/scarv/scarv-soc)
  houses the
  System on Chip (SoC) 
  implementation:
  using the processor core as a central component, the SoC delivers 
  functionality aligned with a micro-controller class device.  More 
  specifically, it adds peripherals including

  - memory (i.e., some [RAM](https://en.wikipedia.org/wiki/Random-access_memory)),
  - communication (e.g., a [UART](https://en.wikipedia.org/wiki/Universal_asynchronous_receiver-transmitter)),
    and
  - randomness generation.

<!--- -------------------------------------------------------------------- --->

## Quickstart (with more detail in the [wiki](https://github.com/scarv/scarv/wiki))

1. Install any associated pre-requisites, e.g.,

   - a modern 
     [LaTeX](https://www.latex-project.org)
     distribution,
     such as
     [TeX Live](https://www.tug.org/texlive),
     including any required packages.

2. Execute

   ```sh
   git clone https://github.com/scarv/scarv.git ./scarv
   cd ./scarv
   git submodule update --init --recursive
   source ./bin/conf.sh
   ```

   to clone and initialise the repository,
   then configure the environment;
   for example, you should find that the environment variable
   `REPO_HOME`
   is set appropriately.

3. Use targets in the top-level `Makefile` to drive a set of
   common tasks, e.g.,

   | Command                   | Description                                                                          |
   | :------------------------ | :----------------------------------------------------------------------------------- |
   | `make build-doc`          | build the [LaTeX](https://www.latex-project.org)-based documentation                 |
   | `make spotless`           | remove *everything* built in `${REPO_HOME}/build`                                    |

<!--- -------------------------------------------------------------------- --->

## Questions?

- read the
  [wiki](https://github.com/scarv/scarv/wiki),
- raise an
  [issue](https://github.com/scarv/scarv/issues),
- raise a
  [pull request](https://github.com/scarv/scarv/pulls),
- drop us an 
  [email](mailto:info@scarv.org?subject=scarv).

<!--- -------------------------------------------------------------------- --->

## Acknowledgements

This work has been supported in part
by EPSRC via grant
[EP/R012288/1](https://gow.epsrc.ukri.org/NGBOViewGrant.aspx?GrantRef=EP/R012288/1) (under the [RISE](http://www.ukrise.org) programme).

<!--- -------------------------------------------------------------------- --->
