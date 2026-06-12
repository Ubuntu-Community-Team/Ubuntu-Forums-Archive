---
title: "My ISP says I have 350,000 inodes and I can't find them"
date: 2021-09-26
forum: New to Ubuntu
---

### Post by jond14799 on 2021-09-26
I built a small website myself using Opencart some years ago to sell specialist parts for old motorcycles and it's always gone well even though it makes hardly any money. I have a very small audience, which suits me as I am retired and recently my health has not been good.

My ISP now wants me to move from a cloud based panel to cpanel but says that because I have about 350,000 inodes they want to move me to a considerably pricier plan.  I started looking at the site's files using Filezilla and then PuTTY but they were the wrong tools.  They advised me as follows:

 > "If you are running on a Windows 10 operating system, you could alternatively install "Ubuntu 20.04 LTS" via the Microsoft Store and when you run it you will directly have an Ubuntu terminal installed on your computer which supports all the necessary commands, including the very common and popular df and du you mentioned about. It is much more powerful tool than PuTTy SSH client is.

   
  Then you could also check the following external guide (for example) for reference on how to gain information about the inodes used, once connected to the server: [https://www.2daygeek.com/linux-check-count-inode-usage/](https://www.2daygeek.com/linux-check-count-inode-usage/) We don't use anything specific. For example the following should display all the files in the current directory and the below directories as well:
   
  ```
find . -printf "%h\n" | cut -d/ -f-2 | sort | uniq -c | sort -rn
```

" (end of quotation)

I have a W10 desktop so I loaded Ubuntu 20.04 LTS and I logged on to their server with 
```
ssh <username they gave me>@<their server name> 
```
and gave the password, and found myself logged in to a terminal interface.
I tried a pwd command which gave the expected answer (judged from the directory tree that Filezilla has always shown me) and then a du command which also worked.  For some reason, the df command was not available to me.  Does that mean it's not available on their server?

I then cut and pasted their find command from the message they sent me, after which nothing further happened.  Expecting that the command might take a while to run if there was indeed 350,000 inodes, I let it run for an hour, when the command prompt had not reappeared.

I then found I could not terminate the command (I tried ctrl C and ctrl Z) or in any way do anything, the session was hung.  I had to close the Ubuntu window.

   I have Googled loads of pages trying to see what to do but the typicsl advice seems to be to install the particular software that the advice-giver is using.  

I have downloaded the total contents of the website to my local machine using Filezilla (the trees below mysql_backups and public_html) and I'm contemplating deleting the whole site and then reloading it from the backups and seeing if that would a) work, and b) get rid of many inodes.  Would that be a sensible thing to try?  Would the site still work?

Some details of the website's files after the download to the Windows machine are:

Total size on disk 30.5MB, number of files 3,042, and 255 directories.  That's hardly large surely?


All email associated with this site has used POP3 (nothing stored on mail servers) and my ISP has told me that the inodes are not linked to email.  They are not telling me where the inodes are though.

So where could the inodes be?

I really am stuck and if push comes to shove I may have to decide to close down the website because I cannot justify the increased costs that I would have to bear if the inode problem is not resolved.

I would really welcome advice on tackling this problem.  Thanks.

---

### Post by GhX6GZMB on 2021-09-26
an inode is very simply explained a directory or a file. 350,000 is not implausible, my Lubuntu laptop is about the same.

---

### Post by DuckHook on 2021-09-26
inodes are not a "problem". They are simply the OS's way of keeping track of all your files and directories. Linux uses a ginourmous number of inodes. Similar to ml9104, my OS uses close to a million. This is distributed between the OS + Apps (315 K), data (484 K) and resource hogs like snaps (200 K). This number does not even include remote LAN servers to which I am linked. They probably number in excess of another million.

[LIST=1]
[*]Before you can get to a solution, you need to clarify in your own mind exactly what your setup is. You have not told us your current setup, but based on your statement: > …and then a du command which also worked. For some reason, the df command was not available to me. Does that mean it's not available on their server?…it is highly probable that your website is built in a Windows environment, and not a Linux one. *du* is present in Windows (though a pale shadow of its Linux counterpart) whereas *df* does not exist in Windows. This explains why you can run *du* but not *df*. You cannot solve Windows problems with Linux solutions.
[*]Your ISP is suggesting that you install an Ubuntu 20.04 LTS virtual machine in order to query your website. However, if your website is built on top of a Windows install, this suggestion makes no sense.
[*]Moreover, it makes even less sense to install an Ubuntu VM just to run *ssh*. *ssh* works by tunnelling a CLI shell into your web server. It doesn't matter whether that shell is the native *ssh* client (Linux) or *PuttySSH* (Windows). Once the *ssh* shell is up and running, you are working in the server's CLI environment. The client OS has no bearing on the server's command structures.
[*]It is also likely that you are conflating your bare 30MB data environment with your whole much larger server install. You need more than just data to host a website—you need a web infrastructure. In your case, this appears to be some sort of Web app on top of Windows. It is more than likely that it is this underlying (and massive) infrastructure that is using up so many inodes.
[/LIST]
It seems to me that yours is really a Windows problem and doesn't belong on this forum. However, I can't be sure of this without more info, hence, I'm leaving this thread in this subforum.

At any rate, I don't see how you can run any sort of website on anything less than 350 K inodes. You may think of your website as "small" but that is just an illusion. The underlying infrastructure needed to run websites, whether large or small, are all more or less the same. In the case of Linux, it involves installing a full blown OS like Ubuntu, then adding the LAMP stack on top of that. That results in a big beast no matter how "small" the website.

---

### Post by jond14799 on 2021-09-27
Thanks to ml9104 and DuckHook for their replies. I will do my best to reply.

Re point 2 from DuckHook: The OpenCart application was built using a browser to fill in forms on an "empty" application installed by the ISP, that's how OpenCart applications are built.  The application itself has no knowledge of Windows and it's PHP based, using a MySQL database plus HTML components.  So there is no history of Windows being used in its construction.

Re point 3: I understand that when I have SSH'ed to my ISP's server, my commands are being run on that, so the absence of the df command does puzzle me.

Re inodes in general, the Wikipedia says that inodes need not have links to anything [https://en.wikipedia.org/wiki/Inode#Implications](https://en.wikipedia.org/wiki/Inode#Implications)  so do they accumulate by proceses finishing abnormally?

---

### Post by rsteinmetz70112 on 2021-09-27
inode probably means index node, but it is a pointer to the location on the filesystem for the information in a file, directory or other thing. The number of inodes is usually fixed when the filesystem is created and the inodes are allocated as new things are added to the file system.  so 350,000 inodes doesn't really mean much as a single inode may or may not be allocated and may point to a large file using a lot of disk space or to something like a pipe or something else using almost no diskspace.

```
df -i <filename>
``` will tell you how many inodes are in a particular file or device. I find it odd that df is not available, it's a pretty standard utility. Were you logging into the Ubuntu on your Windows machine or the ISPs server? If the latter ask them about it.

---

### Post by DuckHook on 2021-09-27
> **jond14799 said:**
> …Re point 2 from DuckHook: The OpenCart application was built using a browser to fill in forms on an "empty" application installed by the ISP, that's how OpenCart applications are built.  The application itself has no knowledge of Windows and it's PHP based, using a MySQL database plus HTML components.  So there is no history of Windows being used in its construction.
Being unfamiliar with OpenCart, this is new (but useful) info. I assume this info is from your ISP. Then, they should also be able to tell you the underlying structure of your website:

[LIST=1]
[*]Does it run its own OS and LAMP stack within a VM or container? Many website hosts do this for security. In my opinion, it is the only safe way to run a website. If so, then it is no surprise that your site will gobble up 350 K inodes.
[*]OTOH, if your ISP implements a "shared" website, hosted with dozens of others on one running instance, then 350K inodes could be excessive. Without a deeper understanding of your use case—i.e. is it heavily transaction based? Highly fragmented? etc—it is not really possible to make definitive conclusions. The only source of more info would be your ISP.
[/LIST]
> Re point 3: I understand that when I have SSH'ed to my ISP's server, my commands are being run on that, so the absence of the df command does puzzle me.
Me too. To my knowledge, both du and df are part of coreutils. To install one is to install the other. But I'm only familiar with Ubuntu. Your ISP may be using another distro which may package its utilities differently.

In any case, based on what you have described so far, it still makes no sense to install an Ubuntu VM just to run ssh.
> Re inodes in general, the Wikipedia says that inodes need not have links to anything [https://en.wikipedia.org/wiki/Inode#Implications](https://en.wikipedia.org/wiki/Inode#Implications)  so do they accumulate by proceses finishing abnormally?
True enough. Orphaned inodes are a thing. If you have lots of them, then you need to hunt down the cause even more than you need to reduce the number. They can arise from lots of causes, but common ones are broken files, not shutting down properly and apps that create massive amounts of temporary files. Since we have no idea of your use case or how OpenCart is implemented, the only people who can really help you here is your website provider.

Do they have a help desk? Perhaps paid one-time expertise?

---

### Post by jond14799 on 2021-09-27
Thanks DuckHook, very helpful.  You pose good questions more authoritatively than I ever could.  I have sent my ISP's support desk the link to this page and am looking forward to hearing from them.  Paid for one-time expertise could be a good way to proceed though I'm not familiar with places to look for it.  A pointer here could help me a lot.  My ISP says I am being moved from cloud hosting to cpanel.  Their terms of reference say "**[FONT=&quot]Storage and Plan Limits for cPanel web hosting.[/FONT]** These Hosting plans are subject to a limit of no more than 250,000 inodes per account for Linux® hosting accounts."  From what I've learnt on this thread, even though the limit sounds like a lot, it doesn't seem to be.
 Jon

---

### Post by DuckHook on 2021-09-27
> **jond14799 said:**
> …Paid for one-time expertise could be a good way to proceed though I'm not familiar with places to look for it.  A pointer here could help me a lot. What I meant by "paid help" is paid help from your ISP. My ISP has an option wherein I can get superior tech support by paying a per&#8209;incidence charge.> My ISP says I am being moved from cloud hosting to cpanel.  Their terms of reference say "**[FONT=&quot]Storage and Plan Limits for cPanel web hosting.[/FONT]** These Hosting plans are subject to a limit of no more than 250,000 inodes per account for Linux® hosting accounts."  From what I've learnt on this thread, even though the limit sounds like a lot, it doesn't seem to be.True enough. When it comes to computing, quantifications don't mean anything without context.

Please appreciate that terms like "cloud" vs "cpanel" are your ISP's pseudo&#8209;marketing terms and don't have much meaning to me. I suspect that other forum members will be just as puzzled unless they use the same product. A quick web search returns more info that makes no sense. It appears that CPanel is merely a web&#8209;hosting control panel. It has no apparent connection to the underlying infrastructure. My reading of it is that CPanel can be installed on a cloud hosted website or a bare metal hosted website, so when your ISP states that it is "moving you from the cloud to CPanel", this is a bit like saying that they are moving you from your apartment to your steering wheel. It implies some underlying change in the infrastructure. Without further explanatory details, it is singularly uninformative.

The general theme should be obvious by now: the only people who can help you decipher all of this is your web hosting service (which happens to be your ISP). We on this forum have no idea how they run their web hosting and would just be blind mice running around in the dark. You need to take your issue up with them and get a fuller understanding of how your site has been hosted up to now and what changing from "Cloud to CPanel" actually means.

---

