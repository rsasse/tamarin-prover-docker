# About

This container runs the [Tamarin prover](https://tamarin-prover.github.io/) which is being used for security protocol verification.
The tool was initially developed at [ETH Zürich](https://ethz.ch/) in Switzerland and is under continuing development on [Github](https://github.com/tamarin-prover/tamarin-prover/).

Many thanks to [eikendev](https://github.com/eikendev) for providing us with this Dockerfile and instructions!

# Usage

We mainly use [Podman](https://podman.io/) to run this image because it's very convenient to run as a normal user.
It aims to provide compatibility with the CLI of Docker, so you should be able to adjust this to your needs.
Here is how we run the container.

```bash
podman run \
	--rm \
	-P \
	-v ./workspace:/workspace \
	--security-opt label=disable \
	--net=host \
	rsasse/tamarin-prover
```

As you can see, a volume is being mapped into `/workspace`.
When mapping files from your file system, make sure to give those files appropriate permissions.

The `--security-opt` flag should only be necessary if your system runs SELinux.

When the container is up, you can visit `http://localhost:3001` and start working on your proofs.
