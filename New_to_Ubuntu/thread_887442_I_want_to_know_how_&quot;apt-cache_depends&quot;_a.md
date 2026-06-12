---
title: "I want to know how &quot;apt-cache depends&quot; and the man page isn't enough"
date: 2008-08-12
forum: New to Ubuntu
---

### Post by tnek on 2008-08-12
The man page of apt-cache has this to say about apt-cache depends:

**depends *[B]pkg**(s)*[/B]
[INDENT]      depends shows a listing of each dependency a package has and all the possible other packages that can fulfill that dependency.
[/INDENT] 
While the output of *[FONT=Courier New]apt-cache depends[/FONT] wget* is:
```
wget
  Depends: libc6
  Depends: libssl0.9.8
  Conflicts: <wget-ssl>

```

I'm wondering what it means that wget-ssl is listed as a conflict? I'm also wondering where I can get more information about *exactly* how apt-cache depends works?

I've searched around on the net but haven't found any more detailed information than what the man page gives me, and that information is sparse to say the least.

As a last resort, is it possible to retrieve the source code for apt-cache so I can browse it and see exactly how depends works? I'm used to programming so I'm not afraid to follow this path if there isn't any other way to get the information I'm seeking.

---

### Post by nicedude on 2008-08-12
I can't answer all your questions but I can tell you what the conflict means. Basically it means you could install wget or wget-ssl, but not both. Sometimes you kinda have to choose which program you want to use to do a certain thing. If you were to use synaptic package manager and search for any given programs in the repositories it will also give you the dependencies, recommended's and what a given program will conflict with. Also synaptic will take care of all the dependencies for you so you won't have to. As far as source code, its open source so yes its available somewhere but I am not sure where to get the exact version source from Ubuntu but someone here will know off the top of their head I am sure.

Hope that helps

---

### Post by niteshifter on 2008-08-12
Hi,

> I'm wondering what it means that wget-ssl is listed as a conflict?
It means that if you have the package wget-ssl installed on your system getting (installing) wget will interfere with wget-ssl's operation, most likely by replacing it. In this specific instance of wget: wget-ssl (if memory serves me right) was invoked by typing / using "wget" - and so is plain wget. I don't know if wget and ssl was important to you or if you're just using it as an example - should it be important: wget from the ubuntu repositories does have SSL/TLS support (can deal with https URLs).

Getting information on _exactly_ how some program works - you've already hit on it - is via source. This is the general form for that:
```
apt-get source <package>
```
Unlike apt-cache, the man page on apt-get has a good amount of detail. Put simply, getting source via this method is akin to getting a tarball (tar-gzip) of the sources into the current working directory. Will get generally the most current source (which may or may not match the binary version you have installed), specific versions can be retrieved and you've the option to download and unpack or just download.

---

