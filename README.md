# BRACKEN OS

**The operating system foundation for BRACKEN.**

BRACKEN OS is the Linux-based system layer intended to run BRACKEN network and infrastructure services on bare-metal hosts and virtual machines. It brings together a configured Linux kernel, base userspace, boot and recovery path, package integration, system services, and security defaults as a maintainable platform.

> **Project status:** Early-stage project. This repository documents the intended scope; implementation, supported hardware, release targets, and operational guarantees are not yet established.

## Goals

- Define a repeatable, supportable base system for BRACKEN nodes.
- Provide consistent boot, installation, upgrade, and recovery behavior.
- Integrate the kernel, drivers, libraries, and required system utilities as a coherent release.
- Apply secure defaults and make system configuration auditable.
- Produce a small, predictable runtime suitable for network appliances and virtual machines.

## Scope

This repository owns the OS configuration and integration: kernel configuration and patches where necessary, bootloader and initramfs integration, filesystem layout, base packages, system service definitions, system identity, installation and recovery tooling, and OS-level hardening.

The product build and image assembly pipeline belongs in [bracken-build](https://github.com/vayun-networks/bracken-build). Shared interfaces and libraries belong in [bracken-core](https://github.com/vayun-networks/bracken-core). Network features belong in their respective service repositories and should integrate through documented OS packages and service contracts.

## Design principles

- Prefer upstream Linux components and small, reviewable changes.
- Keep the base image minimal; optional platform services should remain independently packaged.
- Make configuration declarative where practical and avoid undocumented host mutations.
- Treat upgrades and recovery as first-class operating requirements.
- Record provenance, versions, and security-relevant changes for each image.

## Planned deliverables

The intended evolution is: a reproducible bootable development image; documented system layout and service conventions; installation and recovery flows; an upgrade mechanism with rollback considerations; and release artifacts integrated with the BRACKEN build pipeline. Supported CPU architectures and hardware will be declared only after they are validated.

## Development

No universal build command is defined yet. Build instructions, supported toolchain versions, kernel configuration, and hardware support should be documented here as they become reproducible. Changes that affect boot, storage, networking, privileges, or upgrade behavior should include the rationale and validation environment.

## Related components

- [bracken-build](https://github.com/vayun-networks/bracken-build) — image and release assembly
- [bracken-core](https://github.com/vayun-networks/bracken-core) — shared contracts and libraries
- [bracken-deploy](https://github.com/vayun-networks/bracken-deploy) — provisioning and deployment automation
- [bracken-control-plane](https://github.com/vayun-networks/bracken-control-plane) — node management

## Security

Do not use this system to handle production or untrusted traffic until its threat model, update path, hardening profile, and supported configuration have been reviewed and validated. Report suspected vulnerabilities privately to the maintainers rather than publishing exploit details in an issue.