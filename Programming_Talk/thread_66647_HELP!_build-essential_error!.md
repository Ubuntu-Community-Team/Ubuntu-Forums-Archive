---
title: "HELP! build-essential error!"
date: 2005-09-17
forum: Programming Talk
---

### Post by DiGu182 on 2005-09-17
Hi,
I'm trying to compile many programs and not having success. I tried to do the command:

# sudo apt-get install build-essential

Result:

rodrigo@mark-182:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 3:3.3) but it is not going to be installed
E: Broken packages

What should i do?? PLEASE HELP!!!

---

### Post by Xian on 2005-09-18
[QUOTE=DiGu182]Hi,
I'm trying to compile many programs and not having success.[/quote]
These programs are not in the Ubuntu repositories?

[QUOTE=DiGu182]What should i do?? PLEASE HELP!!![/QUOTE]
What is the output of this command:

```
$ sudo apt-get -f install
```

---

### Post by Roptaty on 2005-09-18
Please post your sources.list file

---

### Post by netunobr on 2005-09-19
I had the same problem..

My sources.list

```

## Uncomment the following two lines to fetch updated software from the network
deb http://archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu hoary universe
deb-src http://archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

deb http://security.ubuntu.com/ubuntu hoary-security multiverse
deb-src http://security.ubuntu.com/ubuntu hoary-security multiverse

## Backports
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

## Marillat
# deb ftp://ftp.nerim.net/debian-marillat testing main

```

---

