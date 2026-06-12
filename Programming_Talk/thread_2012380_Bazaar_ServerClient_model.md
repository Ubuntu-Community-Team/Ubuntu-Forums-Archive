---
title: "Bazaar Server/Client model"
date: 2012-06-29
forum: Programming Talk
---

### Post by jerim79 on 2012-06-29
I am trying to implement some sort of version control at work. I just got finished building us a cloud and I have an Ubuntu 12.04 Server 64bit VM running in the cloud.Setting up Bazaar in the VM seemed almost too easy (apt-get install bzr). 

The question now, is how do we access the server from our desktop machines? We are running Windows 7 and I have installed Bazaar Explorer but there doesn't seem to be a clear cut way of connecting to a server from the Explorer. I see where you can open a URL but it keeps failing when I put in the IP address of my server. 

My co-workers aren't familiar with Linux in general and I want to avoid the command line which they will immediately declare is outdated and cumbersome (somewhat agree).

---

### Post by jerim79 on 2012-06-29
So I create a repository on my Ubuntu machine:
[I]bzr init-repo sample
bzr init sample/trunk[/I]

I go to Bazaar Explorer and try open the URL:
*[http://10.89.97.29/sample.bzr/](http://10.89.97.29/sample.bzr/)*

It tells me it is not a branch, checkout or repository. So I open it as a virtual repository so it can search for nested locations. Then it says:


[I]bzr: ERROR: Transport operation not possible: Transport <bzrlib.transport.http._urllib.HttpTransport_urllib url=http://10.89.97.29/sample.bzr//> has not implemented list_dir (but must claim to be listable to trigger this error). 
[/I]

---

### Post by jerim79 on 2012-06-29
I tried the "Get Project Source From Elsewhere" option. I put in:
*[http://10.89.97.29/bolconsolidation](http://10.89.97.29/bolconsolidation)*

It tells me :
*bzr: ERROR: Not a branch: "http://10.89.97.29/bolconsolidation/".*

I have tried bolconsolidation.bzar and bolconsodliation/trunk

When I try to add a file to the repository from the command line using *bzr add test.txt*, it tells me:
*bzr: ERROR: Not a branch: "/test.txt/".*

---

