---
title: "Vagrant 2.0 timeout"
date: 2017-09-19
forum: Programming Talk
---

### Post by Crafty Kisses on 2017-09-19
I'm trying to access an Ubuntu Vagrant box, just the typical hashicorp one, via 
```
vagrant init hashicorp/precise64
```
Then running 
```
vagrant up
``` 
Then of course, actually SSHing into the box 
```
vagrant ssh
```
I get this error message, I am using the VMWare Fusion provider, which could be the culprit? Although I've looked at the Vagrantfile, and made sure it knows I'm using VMWare Fusion. This is the error message I get
```
monta@users-MacBook-Pro:~$ vagrant up
Bringing machine 'default' up with 'vmware_fusion' provider...
==> default: Checking if box 'hashicorp/precise64' is up to date...
==> default: Verifying vmnet devices are healthy...
==> default: Preparing network adapters...
WARNING: The VMX file for this box contains a setting that is automatically overwritten by Vagrant
WARNING: when started. Vagrant will stop overwriting this setting in an upcoming release which may
WARNING: prevent proper networking setup. Below is the detected VMX setting:
WARNING:
WARNING:   ethernet0.pcislotnumber = "32"
WARNING:
WARNING: If networking fails to properly configure, it may require this VMX setting. It can be manually
WARNING: applied via the Vagrantfile:
WARNING:
WARNING:   Vagrant.configure(2) do |config|
WARNING:     config.vm.provider :vmare_fusion do |vmware|
WARNING:       vmware.vmx["ethernet0.pcislotnumber"] = "32"
WARNING:     end
WARNING:   end
WARNING:
WARNING: For more information: https://www.vagrantup.com/docs/vmware/boxes.html#vmx-whitelisting
==> default: Fixed port collision for 22 => 2222. Now on port 2200.
==> default: Starting the VMware VM...
==> default: Waiting for machine to boot. This may take a few minutes...
    default: SSH address: 172.16.117.136:22
    default: SSH username: vagrant
    default: SSH auth method: private key
Timed out while waiting for the machine to boot. This means that
Vagrant was unable to communicate with the guest machine within
the configured ("config.vm.boot_timeout" value) time period.

If you look above, you should be able to see the error(s) that
Vagrant had when attempting to connect to the machine. These errors
are usually good hints as to what may be wrong.

If you're using a custom box, make sure that networking is properly
working and you're able to connect to the machine. It is a common
problem that networking isn't setup properly in these boxes.
Verify that authentication configurations are also setup properly,
as well.

If the box appears to be booting properly, you may want to increase
the timeout ("config.vm.boot_timeout") value.
```

---

### Post by 3djake on 2017-10-01
I lack experience in Vagrant, although I have used it before.

Can we see your vagrant file? (make sure to remove public IP's you do not want us to see)

---

