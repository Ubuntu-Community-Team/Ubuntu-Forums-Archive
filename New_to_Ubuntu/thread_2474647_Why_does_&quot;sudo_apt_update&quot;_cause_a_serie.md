---
title: "Why does &quot;sudo apt update&quot; cause a series of errors?"
date: 2022-05-04
forum: New to Ubuntu
---

### Post by Complete on 2022-05-04
I have a Ubuntu 22.04 virtual machine using VMware on a Windows 10 Enterprise computer.
Part of setting things up requires I use the command"

> [FONT=Courier New]sudo apt update[/FONT]

or

> [FONT=Courier New]sudo apt-get update --fix-missing[/FONT]

both commands cause the same error messages.  They consist of

> [FONT=Courier New]403  Forbidden [IP: 91.189.91.39 80][/FONT]

Either I need to do something to establish a network connection, I assume, or I need to find a way to do what I need through downloads and file shares with the host computer.  Either way, I need help.

Since I do not have the ability to share files or the clipboard memory with the Virtual Machine, I had to do a screen shot.  But, fortunately, I ran that through a pretty good OCR image to text converter so I can share this:
> 
william@wtiltam-virtual-machine: - $ sudo apt update 
[sudo] password for wtlltam: 
Err:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jamay InRelease
403 Forbidden (IP: 91.189.91.39 80] 

Err:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease
403 Forbidden [IP: 91.189.91.39 86] 

Err:3 [http://us.archive.ubuntu.coR/ubuntu](http://us.archive.ubuntu.coR/ubuntu) jaray.backports InRelease
403 Forbidden [IP: 91.189.91.39 80) 

Err:4 [http://securtty.ubuntu.com/ubuntu](http://securtty.ubuntu.com/ubuntu) jammy-security InRelease
403 Forbtdden [IP: 91.189.91.38 80] 

Reading package lists... Done 
N: See apt-secure(8) manpage for reposttory creatton and user conftguration detatls. 
N: Updating from such a reposttory can't be done securely, and ts therefore disabled by default. 
E: The reposttory 'http://us.archive.ubuntu.coR/ubuntu jammy InRelease' ts no longer signed. 
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jarmy/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/jarmy/InRelease) 403 Forbidden [IP: 91.189.91.39 80] 
N: See apt-secure(8) manpage for repository creation and user configuration detalls. 
N: Updating from such a reposttory can't be done securely, and is therefore disabled by default. 
E: The repository 'http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease' is no longer stgned. 
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease) 403 Forbtdden [IP: 91.189.91.39 80) 
E: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease](http://us.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease) 403 Forbtdden [IP: 91.189.91.39 80] 
E: The repository 'http://us.archive.ubuntu.com/ubuntu jarmy-backports InRelease' is no longer signed.
N: Updating from such a reposttory can't be done securely, and is therefore disabled by default. 
N: See apt-secure(8) manpage for reposttory creation and user configuration detalls. 
E: Falled to fetch [http://security.ubuntu.com/ubuntu/dists/jarny-securtty/InRelease](http://security.ubuntu.com/ubuntu/dists/jarny-securtty/InRelease) 483 Forbidden [IP: 91.189.91.38 80 ] 
E: The repository 'http://security.ubuntu.com/ubuntu jammy-securtty InRelease' is no longer signed. 
N: Updating from such a repository can't be done securely, and is therefore disabled by default. 
N: See apt-secure(8) manpage for reposttory creation and user configuration detalls. 

william@william-virtual-machine:


And here is a link to the screen capture

[https://photos.app.goo.gl/7cK5hYeKHFwyr5ne6](https://photos.app.goo.gl/7cK5hYeKHFwyr5ne6)

Please help

---

### Post by TheFu on 2022-05-04
Well, the IP address above isn't a proper IP.  IPs are in the x.y.z.a format. No :, unless they are IPv6 and IPv6 IPs don't use '.' separators.
Something is wrong in the network config.

Until you can **ping 1.1.1.1**, you won't be able to update the package lists. Networking, at least connectivity to the internet, is broke until that is possible.

---

### Post by Complete on 2022-05-04
> **TheFu said:**
> Well, the IP address above isn't a proper IP.  IPs are in the x.y.z.a format. No :, unless they are IPv6 and IPv6 IPs don't use '.' separators.
Something is wrong in the network config.

Until you can **ping 1.1.1.1**, you won't be able to update the package lists. Networking, at least connectivity to the internet, is broke until that is possible.

I made some mistakes in the OP and I will update it.

---

### Post by guiverc on 2022-05-05
Question also asked at [https://askubuntu.com/questions/1406691/why-does-sudo-apt-update-cause-a-series-of-403-connection-errors](https://askubuntu.com/questions/1406691/why-does-sudo-apt-update-cause-a-series-of-403-connection-errors)

There are obvious typos/errors in your paste; are those really there?  as *jammy* and *jamay* are different words thus errors are to be expected..

---

### Post by TheFu on 2022-05-05
> **Complete said:**
> I made some mistakes in the OP and I will update it.

Rather than doing text captures as images, please learn to use the **tee** command and redirection. That way you'll have the EXACT output - no OCR, no re-typing, no human mistakes in the output ... er, unless you grab the wrong file or had the wrong command or options.  We all do these things from time to time.

For example, to see the output from any command AND send that output to a file, use
```
$ sudo apt-get update --fix-missing 2>&1 | **tee** /tmp/a-update-out
```

That file will contain the output with both stdout and stderr. It overwrites any prior content. There is a way to append, but I'll leave that for you to figure out.  Worst case, use a flash drive to copy the file off the system, if local networking isn't working.

Using redirection is a core Linux skill. Learn it, understand it, love it!  That 2>&1 is just 1 method of redirection. There are others for different needs. Very worthwhile to learn to send stdout to 1 file and stderr to a different file, for example.

We don't need to see 50 lines without errors.  We need to see the command and a few lines after it, then ....   a few lines before the errors start, a few of the first errors (never need to see 50 lines of the same error, just a few), then how the command ends and the final errors.

What we do with that is take the program and the error, then put it into google and search. Almost always in the top 3 results will be possible problem and a solution for it to try. Sometimes, there are pages and pages of answers.  Be careful visiting random web-blogs for answers.  Try to find answers from domains that have "ubuntu" in the name, not just anywhere in the URL. Also, look for answers for the exact version of Ubuntu you are running.  Exact version is the release number AND the DE.

---

### Post by ActionParsnip on 2022-05-05
Yep. Bad typing will cause issues

---

### Post by Impavidus on 2022-05-05
Typos aren't present in the screenshot.

403 is an error response generated by the server. Your computer has no problem contacting the server, which appears to be the right one based on its name, but the server doesn't give the expected response. I don't know how this being a virtual machine may interfere with this. The address looks OK, but there may be a problem with the way your virtual Ubuntu system access the network. That server usually works fine.

What's in your /etc/apt/sources.list? An error there may also explain this.

---

### Post by ActionParsnip on 2022-05-06
Do you use a proxy for web access?

---

