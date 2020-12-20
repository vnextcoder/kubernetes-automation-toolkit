# Quickstart with Vagrant on your PC

Follow these steps to quickly deploy the KAT example. You will need a PC with at least 4 cores and 8 GB of RAM  to run KAT locally in a VM that Vagrant will setup for you; if you don't have such a machine then please  use a cloud provider to rent a VM (although you may be able to get a limited time free VM). We provide instructions for this alternative [here](./cloudvm.md).

1. Install [Hashicorp's Vagrant](https://www.vagrantup.com/downloads) for your OS.

2. Navigate to the root directory of the KAT repository and enter this command in a terminal
```bash
vagrant up
# Please be patient, even on a fast Internet connection remember we are downloading and installing over 2GB of OS, Kubernetes, docker images etc.
```

3. You can now open a web-browser and reach these end-points
  - Todo application Vuejs Frontend [http://localhost:8080/frontend/](http://localhost:8080/frontend/)
  - Todo application browsable API [http://localhost:8080/djangoapi/api/v1](http://localhost:8080/djangoapi/api/v1)
  - Kubernetes Dashboard [http://localhost:8080/dashboard/](http://localhost:8080/dashboard/)
  - Grafana Monitoring [http://localhost:8080/monitoring-grafana/](http://localhost:8080/monitoring-grafana/)


4. Get the ssh-configuration snippet for your Vagrant VM and add it to your `~/.ssh/config` file; these commands will do this:
```bash
#For Linux, Mac you could run
vagrant ssh-config >> ~/.ssh/config

# For Windows
vagrant ssh-config >> ~\.ssh\config
```
Confirm that you can now log into the Vagrant VM by simply typing `ssh default` on the commandline.

5. Once you are logged into the VM there are many things to do
  - Launch [k9s from the terminal](https://k9scli.io/) and surf your Kubernetes cluster and all its objects.
  - If you prefer using the official Kubernetes CLI  then  read the `kubectl` cheat-sheet [here](https://kubernetes.io/docs/reference/kubectl/cheatsheet/).

6. Head over to our [documentation](./README.md) to learn the concepts and start understanding the code behind the components..


***The next steps are optional but very useful if you are planning to get productive as a developer***

7.  We assume you use the [Microsoft VS Code Editor](https://code.visualstudio.com/Download) in this tutorial, please install the [Remote - SSH plugin](https://code.visualstudio.com/docs/remote/ssh). This will allow us to browse and control the Vagrant VM via SSH.

8. Open VS Code and configure it to connect remotely to the Vagrant VM. Load up the KAT code in the home directory of the Vagrant user. Tweak it, break it, fix it and choose whether this way of development will work for you!

## Cleanup

To destroy the Vagrant VM, open a terminal and go to the kubernetes-automation-toolkit (root directory of the git repository where the Vagrantfile lives) and simply type

```
vagrant destroy
```