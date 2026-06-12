---
title: "Ubuntu Core + OS updates for IOT project"
date: 2021-04-21
forum: New to Ubuntu
---

### Post by chris-yu on 2021-04-21
We are considering to use Ubuntu OS on a IoT project that will have 1500 devices in the field. 

Have a few questions, would love some help: 

[LIST]
[*]From the Ubuntu Core docs it's not clear how we actual install and manage the devices in a scalable manner.
Previously we've used [balena.com]("http://balena.com/")  which lets us deploy a docker image to a device. We flash the Balena image to a device, that device then connects to Balena, registers itself and downloads and runs our app (as a docker image).
[*]When we push container updates they are automatically deployed to all devices (or when triggered, for gradual rollout).
[*]When needed we can see live logs from devices or open a remote console on a device to do further debugging. We need to do some complicated network config in this project - connect via 4G Modem, then connect an IPSec VPN, then NAT local devices over either the VPN or the 4G connection. How can we do equivalent things using Ubuntu Core?
[*]When looking at the ubuntu core docs [https://ubuntu.com/core/docs/using-core](https://ubuntu.com/core/docs/using-core) they talk about SSHing in to a device. We need to be able to do these sorts of task preferably from a web UI rather than SSHing to each device. What is the tool(s) in Ubuntu can help us with this?
[/LIST]

Thanks for your help in advance.

---

### Post by grahammechanical on 2021-04-21
I have the feeling that the members of this forum can offer you little help. How many of us have even experimented with Ubuntu Core let alone have experience in large scale deployment?

I, a home user, experimented with Ubuntu core 16 in 2017. I was limited by the fact that I did not have a device to install it on. I succeeded in installing Ubuntu core to a second hard disc and to a USB memory stick. But discovered that we cannot SSH from a loaded OS on one hard disc into an OS on a second hard disc because the second OS was not loaded into memory.

Ubuntu core does not come as an ISO image. The latest image is ubuntu-core-20-amd64.image.xz. This is, of course, for amd64 compatible CPUs. I got it onto a hard drive using image restore function in file manager.

There are different Ubuntu core images for different device hardware and the installation methods most likely will be different. Is your hardware listed here under Ubuntu for IoT?

[https://ubuntu.com/#download](https://ubuntu.com/#download)

It is even possible to build your own image and Canonical will work with organisations to craft images for hardware that is not specifically supported.

Ubuntu Core 20 is a snap based OS. Any application that you want to run on it will have to be a snap packaged application. You can have your own company snap store to put your company snap application in and push out updates to the snap. 

The Ubuntu core OS is itself a snap. Updating both the OS and any snap apps for a single device is done through running a command on Ubuntu core. I have no idea how it is done for multiple devices. But Canonical claims it can be done and names several major commercial organisations already doing it. I come to the conclusion that the people to consult with are the Ubuntu core developers at Canonical. Or, rather the relevant Canonical sales team that would like your business. See the "contact us" links in this web page.

[https://ubuntu.com/core](https://ubuntu.com/core)

I have given you the best I could offer. There may be others on this forum who can give better help.

Regards

---

### Post by him610 on 2021-04-23
If anyone can help the OP, it is TheFu.

---

