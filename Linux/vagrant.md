**Vagrant is a tool for building and managing virtual machine environments in a single workflow**

---

**Install vagrant on Windows/Linux/macOS**

- [Go to this URL](https://www.vagrantup.com/) and install for your operating system

---

**Vagrant command:**

- [Find Boxes](https://app.vagrantup.com/boxes/search)
- Create one folder anywhere on your computer
- Inside this folder create 2 folders. One for Ubuntu and another for CentOS (Practice for this OS)
- Two ways we can create a box
  - vagrant init ubuntu/trusty64
  - It create vagrant file
    ```
    # -*- mode: ruby -*-
    #vi: set ft=ruby :
    Vagrant.configure("2") do |config|
      config.vm.box = "ubuntu/trusty64"
    End
    ```
  - Now we use this command to create a VM
    ```
    Vagrant up
    ```
- Here first download the box using this command
  ```
  vagrant box add ubuntu/trusty64
  ```
- Then write the below command. It takes laser time because already we have downloaded it from the cloud and store in the local machine
  ```
  vagrant init ubuntu/trusty64
  ```
- Create a minimal Vagrantfile (no comment or helpers )
  ```
  vagrant init -m ubuntu/trusty64
  ```
- Create a new Vagrantfile, overwriting the one at the current path
  ```
  vagrant init -f ubuntu/trusty64
  ```
- List the downloaded boxes
  ```
  vagrant box list
  ```
- Remove Box
  ```
  vagrant box remove [box_name]
  ```
- Start Virtual Machine
  ```
  vagrant up
  ```
- Halt Virtual Machine
  ```
  vagrant halt
  ```
- Destroy your Virtual Machine

  ```
  vagrant destroy
  ```

  - The source code and the content of the data directory will remain unchanged. Only the Virtual Box machine will be destroyed. You can build your machine again with the
    ```
    vagrant up
    ```
    command.

  **Command for single and multiple machine creation**

  - Single machine create

    ```
    Vagrant.configure("2") do |config|
      config.vm.define "machine1" do |vb3|
      config.vm.box = "archlinux/archlinux"
      vb3.vm.hostname = "r1"
      vb3.vm.provider "virtualbox" do |v3|
      v3.name = "machine1"
    end
    end
    end

    ```

  - Double machine create

        ```
        Vagrant.configure("2") do |config|
          config.vm.define "machine2" do |vb2|
          config.vm.box = "archlinux/archlinux"
          vb2.vm.hostname = "r2"
          vb2.vm.provider "virtualbox" do |v2|
          v2.name = "machine2"

        end
        end

          config.vm.define "machine3" do |vb3|
          config.vm.box = "archlinux/archlinux"

          vb3.vm.hostname = "r3"
          vb3.vm.provider "virtualbox" do |v3|
          v3.name = "machine3"
        end
        end

        end
        ```

  - In the same way we can create multiple machine with a single command file
