---
title: "man pages for C functions"
date: 2008-05-14
forum: Programming Talk
---

### Post by Wim Sturkenboom on 2008-05-14
Which package do I need to install to get the man pages for the standard C functions like fgets etc?

I can compile (whichever packages they are, they're there), but I'm desperately missing my man pages.

If you need to know what is installed, please give me the CLI command to find it.

Thanks WimS

PS Dapper Drake in case it's relevant.

---

### Post by MaindotC on 2008-05-14
I think you need the build-essential package that usually comes pre-installed.  I couldn't find fgets or scanf, but I could do:
```

man printf

```
and it returned a man page.

---

### Post by Wim Sturkenboom on 2008-05-14
Yes, the wrong one (*man 1 printf* I think)

---

### Post by MaindotC on 2008-05-14
The package is called manpages-dev.  I found them by googling "c functions man pages" and it was the first [thread]("http://ubuntuforums.org/showthread.php?t=283391") that appeared.

---

### Post by Wim Sturkenboom on 2008-05-14
Thanks; I should have googled myself, but I'm getting fed-up with Ubuntu as it never seems to provide directly what I'm looking for.

I mean, how do you know what to download; even the search (*c functions*)in synaptic does not show this specific package. I did find glibc-doc earlier and installed it but that did not do the trick.

---

### Post by MaindotC on 2008-05-14
Well I'm sorry you feel that way and I hope you find something that suits your needs :(

---

### Post by LaRoza on 2008-05-14
> **Wim Sturkenboom said:**
> Thanks; I should have googled myself, but I'm getting fed-up with Ubuntu as it never seems to provide directly what I'm looking for.

I mean, how do you know what to download; even the search (*c functions*)in synaptic does not show this specific package. I did find glibc-doc earlier and installed it but that did not do the trick.

Using Linux takes getting used to. You can't expect to be familiar with all *nix tools and conventions in a short period of time. 

My search terms:

```

apt-cache search manpages

```

Yielded useful information. Once you get used to the naming conventions of packages, it is easier to search.

In case you don't know, the development package is "build-essential". Ubuntu is weird in that it comes without build-essential and the development man pages. Many distros come with them.

---

### Post by Wim Sturkenboom on 2008-05-14
@strAlan:
Ubuntu suits my needs for the desktop very well (I'm using it since Warty Warthog) and I'm not planning to dump it for another desktop distro in the near future. I however like to be able to develop on it as well and that seems to be a mission as the repos don't seem to make sense to me.

Slackware suits my needs for servers to (near) absolute perfection as well as for programming. It however does not suit my needs for the desktop.

@LaRoza
Thanks for the CLI command; found another package that I more than likely will need (related to posix).

The first thing that I installed was build-essential. I don't have a clou why I did it (probably as it's often mentioned on Ubuntuforums) as reading the description for build-essential clearly states that you only need it if you want to create debian packages; it also states that it's only an informational list. If I remember correctly, it did not bring the gcc and maybe only a few (possibly none) of the expected manpages.

PS why is there no icon so I can thank you (ah, now there is)

---

### Post by LaRoza on 2008-05-14
> **Wim Sturkenboom said:**
> Ubuntu suits my needs for the desktop very well (I'm using it since Warty Warthog) and I'm not planning to dump it for another desktop distro in the near future. I however like to be able to develop on it as well and that seems to be a mission as the repos don't seem to make sense to me.

Slackware suits my needs for servers to (near) absolute perfection as well as for programming. It however does not suit my needs for the desktop.

Once you get all the packages, it should work fine.

The development files are named with a "-dev" suffix. So for Finch, the package name is "finch" and its development files are "finch-dev". (Likewise, the "manpages" package has the "manpage-dev" package.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/) is a good place for search also.

Good luck!

---

