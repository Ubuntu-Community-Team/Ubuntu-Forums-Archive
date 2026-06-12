---
title: "OpenSSL Server Heartbeat or Heartbleed vulnerability"
date: 2014-04-08
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2014-04-08
In a hurry? See my question under the --------------- line.

I follow [Falko Timme]("http://www.falkotimme.com/")'s Twitter feed and am glad I do, even thought I'm an end user of Ubuntu. Today, Mr. Timme warned of an attack vector to #Openssl #Heartbleed #vulnerability. [ATTACH=CONFIG]251834[/ATTACH]

I opened the link "[How To Find Out If Your Server Is Affected]("http://www.howtoforge.com/find_out_if_server_is_affected_from_openssl_heartbleed_vulnerability_cve-2014-0160_and_how_to_fix")"

and, even though I cannot recall ever installing something named: OpenSSL, I was surprised to see that this package is installed on my home desktop box, which I, AFAIK, does NOT serve anything whatsoever.

To be safe, I ran:

```
sudo update
sudo upgrade
```

and then had a look at the version:

```
openssl version
```

```
mark@Lexington:~$ dpkg-query -l 'openssl'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  openssl        1.0.1-4ubuntu5 Secure Socket Layer (SSL) binary and related
```

As Mr. Timme's SourceForge page specified "your server might be vulnerable as the version is below **1.0.1g**. " And I cannot understand what package I have installed as the return from dpkg shows only 4ubuntu5 and not the alphabet revision, I'm frankly worried my computer may be vulnerable.

I have also read these relevant pages to this attack vector:

[USN-2165-1: OpenSSL vulnerabilities]("http://www.ubuntu.com/usn/usn-2165-1/")

[Upgrades]("https://wiki.ubuntu.com/Security/Upgrades")

I don't want to upgrade from Ubuntu Ver. 12.04LTS (Precise Pangolin) until the whole Ubuntu community does. (I'm a computer follower, not leader), so:

-------------------------------------------------

What package of Openssl is installed on my computer? Is it a package that is vulnerable? It if is vulnerable is there a fix other than upgrading from 12.04?

---

### Post by kostkon on 2014-04-08
If you have already read the usn, why are you worried about that? If you have already installed the update you are fine. Upgrades in this case mean package upgrades, not distribution upgrades.

Thus, your system is not vulnerable anymore, as the usn says, all the supported packages have been patched already. To make sure try giving
```
openssl version -a
```
and check the build date.

Obviously you are fine and you don't need to upgrade to a newer ubuntu version.

---

### Post by Mark_in_Hollywood on 2014-04-08
mark@Lexington:~$ openssl version -a
OpenSSL 1.0.1 14 Mar 2012
built on: Mon Apr  7 20:33:29 UTC 2014

Case Closed. Thanks.

---

### Post by Damico on 2014-04-08
I'm confused about this being solved because I just tried to update my openssl, and it failed to update to the patched version:
- [What should we users do immediately about the heartbleed heartbeet openssl saucy flaw]("http://ubuntuforums.org/showthread.php?t=2215886&highlight=heartbleed")

---

### Post by bthiyagu1979 on 2014-04-11
Thanks. working fine

---

### Post by SeijiSensei on 2014-04-11
> **Damico said:**
> I'm confused about this being solved because I just tried to update my openssl, and it failed to update to the patched version:
- [What should we users do immediately about the heartbleed heartbeet openssl saucy flaw]("http://ubuntuforums.org/showthread.php?t=2215886&highlight=heartbleed")

Only [currently supported versions]("https://wiki.ubuntu.com/Releases") of Ubuntu will be upgraded.  That includes 10.04 Server, 12.04 LTS, 13.10, and 14.04 LTS.  Any releases before 13.10 other than 10.04 Server are no longer supported.  That's why most people should be using an LTS version.

---

