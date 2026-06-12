---
title: "Notepad++ like editor with multiple ftp connections"
date: 2018-10-17
forum: Programming Talk
---

### Post by dlalonde2 on 2018-10-17
Right now I'm using Notepad++ on Ubuntu. I've also used Geany but what's missing is a proper FTP manager like there is with NppFTP. I can mount the FTP servers in Nautilus of course but I already have in excess of 10 connections.

Is there an editor that offers that? If not is there a way to do this?

Thanks!

---

### Post by TheFu on 2018-10-17
You probably won't like my answer.

FTP is a dead protocol.  It should have been removed in 1995 when telnet and rlogin were effectively killed off.

If you are dead set on using FTP, stop reading.

For transferring files, there are multiple other solutions these days that don't send passwords unencrypted.  I don't know which is best for you, but some ideas:
* rsync
* scp 
* sftp
or
using some sort of DVCS like git.

The last option, git, has been taking over most web dev processes the last few years.  The other options are based on ssh and use ssh-keys for authentication.  Using password-based authentication is considered a security failure and has been for the last 15+ yrs.

Lots of editors support using rsync, sftp and git, but I'd suggest you just create a little script that does what you want, since a professional website would automatically generate any graphical assets in an optimized way and compress and dynamic code to make page access and loading more efficient.

BTW, pretty much any file manager in Linux supports the sftp:// URL, if you want to treat it just like plain FTP, but will honor ~/.ssh/config settings and keys.

Scripting is much more efficient, IMHO, and frees you from some GUI that will change in ways you have no control over.
If the webhost only supports plain FTP, it is time to fire them. The fact that they allow anyone to use plain FTP is a real concern. 

But regardless, please don't use plain FTP anymore. It is a security nightmare except on a private network with no other users.

---

### Post by dlalonde2 on 2018-10-17
> **TheFu said:**
> You probably won't like my answer.

FTP is a dead protocol.  It should have been removed in 1995 when telnet and rlogin were effectively killed off.

If you are dead set on using FTP, stop reading.

For transferring files, there are multiple other solutions these days that don't send passwords unencrypted.  I don't know which is best for you, but some ideas:
* rsync
* scp 
* sftp
or
using some sort of DVCS like git.

The last option, git, has been taking over most web dev processes the last few years.  The other options are based on ssh and use ssh-keys for authentication.  Using password-based authentication is considered a security failure and has been for the last 15+ yrs.

Lots of editors support using rsync, sftp and git, but I'd suggest you just create a little script that does what you want, since a professional website would automatically generate any graphical assets in an optimized way and compress and dynamic code to make page access and loading more efficient.

BTW, pretty much any file manager in Linux supports the sftp:// URL, if you want to treat it just like plain FTP, but will honor ~/.ssh/config settings and keys.

Scripting is much more efficient, IMHO, and frees you from some GUI that will change in ways you have no control over.
If the webhost only supports plain FTP, it is time to fire them. The fact that they allow anyone to use plain FTP is a real concern. 

But regardless, please don't use plain FTP anymore. It is a security nightmare except on a private network with no other users.

Thank you for your answer. I was kind of expecting that type of answer. ;)

We're in the process of moving things to Git but until then we have to use FTP. Once we're on Git I'll just install a LAMP server on my computer and use pushes and pulls to get the files on the remote server.

I don't understand what you mean by "but I'd suggest you just create a little script that does what you want, since a professional website would automatically generate any graphical assets in an optimized way and compress and dynamic code to make page access and loading more efficient".

---

### Post by TheFu on 2018-10-17
git works over ssh, so you can use any of those other solutions already.  rsync between different systems, uses ssh by default.

Websites have different sorts of assets. These all need to be optimized, tested, validated for a variety of reasons before being placed into production.  That means some sort of workflow that is repeatable. Repeatable processes don't have humans point-n-clicking more than 1 thing.  These days, many deployment workflows are caused automatically just because software was checked into the version control system.  [https://jenkins.io/](https://jenkins.io/) is one of those solutions. There are others.

* Images need to be optimized for size and color depth for web viewing.
* client-side layout files need to be compressed for efficient transfer and use.
* client-side scripting files, need to be compressed and probably obfuscated for efficient transfer and to prevent trivially being stolen by competitors.
* all code needs to be put through coding standards enforcement, linters, security reviews, validation suites and fuzzing testing before being placed into production.
These are things that good shops do as part of their workflows. They can't be skipped easily.

For pushing code to production, the developer should never be involved. It should always be a support person. The developer shouldn't have access to production systems at all.  This is harder to do in tiny companies, but if there are 10 people in a company, then the devs really shouldn't need access to production systems.  It also means that developers are farther away from production issues and don't need to be on-call.

I've worked places with huge teams (500+ programmers), 20, 10, 5, 3, and 1 (just me).   When it is just me, all my failings are cause for concern.  I'm far from perfect and my issues lacking knowledge is new areas shows.  With 5 developers and a operations team, I pressed for zero developer access to any pre-prod or production systems.  That ensured "1 quick fix" was never missing from version control and it ensured that automatic testing was run to prevent regression failures.  
Some places use "continuous integration / continuous deployment" as a way of life.  I'm not a fan of the CI/CD method, but I do like weekly deployments for websites that don't impact human lives.  Of course, if the site is mainly dealing with cat videos, push changes 50x a day if you like.  E-911 systems and aircraft control systems need more careful testing, right? 

Anyway, it is your baby. A little scripting would likely make life easier assuming you don't go 100% CI/CD.  Repeatable processes are good. They can be incrementally improved and prevent mistakes by humans from happening more than 1-2 times.  Deming would be proud.  [https://en.wikipedia.org/wiki/W._Edwards_Deming](https://en.wikipedia.org/wiki/W._Edwards_Deming)

---

