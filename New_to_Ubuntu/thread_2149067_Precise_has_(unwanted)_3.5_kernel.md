---
title: "Precise has (unwanted) 3.5 kernel"
date: 2013-05-27
forum: New to Ubuntu
---

### Post by exiztone on 2013-05-27
I installed 12.04.2 x86-64. I had problems installing AMD drivers and couldn't work out why, then I see when I do a uname -a
```
Linux t400 3.5.0-31-generic #52~precise1-Ubuntu SMP Fri May 17 15:27:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```
Is this right? I thought that Precise should have a [3.2 kernel]("http://distrowatch.com/table.php?distribution=ubuntu") (which would be compatible with the graphics driver).

Can I downgrade to a 3.2 kernel?

---

### Post by deadflowr on 2013-05-27
On precise the 3.5 kernel series is called lts-quantal and should be an option, but not a mandatory install.
If you run synaptic you should be able to remove and downgrade to the 3.2 series.
I run precise and my kernel series is 3.2.

---

### Post by exiztone on 2013-05-27
Thank you. I did a bit of Googling and it seems that with the 12.04.2 release the *linux-image-generic-lts-quantal* package is installed by default. This was a bit unexpected.

---

### Post by sudodus on 2013-05-27
I have the same kernel as you, and it is how it should be. It was upgraded along the way (I don't remember if it was at the first or second point release).

```
sudodus@April-2013:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise
sudodus@April-2013:~$ uname -a
Linux April-2013 3.5.0-31-generic #52~precise1-Ubuntu SMP Fri May 17 15:27:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
sudodus@April-2013:~$ 
```

*Edit*: Unless, of course if you have problems with the graphics driver. Then you can reinstall the old kernel
for example version 3.2.0-44 which I think is the newest of the 3.2 versions.

---

### Post by deadflowr on 2013-05-27
> **sudodus said:**
> I have the same kernel as you, and it is how it should be. It was upgraded along the way (I don't remember if it was at the first or second point release).

```
sudodus@April-2013:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise
sudodus@April-2013:~$ uname -a
Linux April-2013 3.5.0-31-generic #52~precise1-Ubuntu SMP Fri May 17 15:27:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
sudodus@April-2013:~$ 
```

*Edit*: Unless, of course if you have problems with the graphics driver. Then you can reinstall the old kernel
for example version 3.2.0-44 which I think is the newest of the 3.2 versions.

Well myself, I haven't seen an upgrade to 3.5.
But for the op, at this point in time, you are given a choice to either go with an older kernel (3.2) or newer kernel (3.8)
The raring kernel is now available on precise.

---

### Post by ibjsb4 on 2013-05-27
If you like/think that the 3.2 kernel is better suited for your needs, then why not just install it?  Not saying this is the answer for everyone, but Im running 12.04.02 and the 3.2 kernel without issues.  I find keeping track/adding/removing kernels with [synaptic package manager]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9") an easy way to go.

Also did you know the 3.8 kernel is now in the repositories?

---

### Post by ajgreeny on 2013-05-27
I installed Xubuntu 12.04.2 at the end of March, and that gave me the 3.2.0-## kernel by default.  I have now, however updated to the 3.5.0-## version, but I had to install that manually as it was not offered by default.

I do not use update-manager to update my system, but prefer to use synaptic when the notifications appear, and I don't know if that makes any difference to the defaults offered, or if it is Xubuntu that has different updates from Ubuntu.

I also tried the 3.8.0-## version and apart from minor lightdm glitches just before the login screen, that also seemed to work well.  However, because of those minor problems and my fear that it may cause some other instability I uninstalled that 3.8 kernel, and now run faultlessly with the 3.5.
```
$ version
Description:    Ubuntu 12.04.2 LTS
Codename:    precise
Desktop:    xubuntu
Linux Xubuntu 3.5.0-31-generic #52~precise1-Ubuntu SMP Fri May 17 15:27:06 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```
PS:
If anyone is interested in how I got that output, I have an alias ```
alias version='lsb_release -dc && echo "Desktop:    $DESKTOP_SESSION" && uname -a'
```

---

### Post by gifford on 2013-05-27
What problems were you having with the AMD graphics driver?
On my system, which is 12.04.2, the AMD FGLRX, under system settings, additional drivers is listed as "This driver is activated but not currently in use".
This is an error and is related to jockey. When I use the command "fglrxinfo" it reports the driver is in use and I have had no problems in use. 
I have reported this as a bug as it seems to be related to the jockey package.
The 3.5x kernel is what I am using.

---

### Post by deadflowr on 2013-05-27
Curious question, though.
How long is the support for the lts-quantal/raring kernels for?
Is it for the length of the quantal/raring support, or the length of precise?

---

