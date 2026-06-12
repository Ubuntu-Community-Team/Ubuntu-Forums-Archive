---
title: "SyncThing as service with folderpath on encrypted drive"
date: 2021-02-28
forum: New to Ubuntu
---

### Post by amarok74 on 2021-02-28
Hello, I have the following setup:

Client: Mac Mini with Syncthing 
Server: Ubuntu 20.04 Desktop with Syncthing

My goal is to run Syncthing as a service on the server, so that it starts automatically after startup without user login. With that my client would automatically sync its files to the server as soon as its started.

I installed Syncthing on both machines and it runs well. I also managed to start Syncthing as a service on the ubuntu box.

The only problem I have is the following: The folder path for Syncthing on ubuntu is on a encrypted disk. When I login and start Syncthing manually this is no problem, but when Syncthing starts after reboot as a service it gets an error “path not found”

How can I access the folder on the encrypted disk during system startup (or better: without user login)? Or is there another solution?

Thanks for your help 
Jürgen

---

### Post by amarok74 on 2021-02-28
Hi, I found the solution myself:

In the "Disks" application one can edit the "Encryption Options" and set the drive to "unlock at system startup". 

BR
Jürgen

---

