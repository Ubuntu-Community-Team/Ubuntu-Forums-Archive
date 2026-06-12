---
title: "non persistent home directory  / web passwords"
date: 2024-07-13
forum: New to Ubuntu
---

### Post by seanhaynes1 on 2024-07-13
Afternoon all, hope you are well...

Though my understanding of all thing Linux is limited I can usually muddle through...but it's been a while.

Senario: I work for a charity supporting people who suffer with mental health conditions , our budgets are very limited so I need to eek out as much as I can from the hardware we have. I have a load of old laptops that can no longer run Windows, so thought I could re-purpoase then to run Ubuntu desktop. The default image runs great. 
We have people who man the Crisis lines 24/7, all the services they use are cloud based ,so really only need these machines to access online services - no local stuff. The services they access hold persoanl information on clients/ users of the Crisis line. The laptops will be shared amongst both employed staff and volunteers as required , so not assigned to an individual user.

My plan was to create a standard Guest account with the primary focus being that the machine does not cache user passwords to the online sites, so if the laptop gets swipped etc access to client data is assured. So doing a bit of research I found Ligthdm which did the job brilliantly but, none of the browsers worked - I 'think' as they could not write to tmp folders?
So in my little head I was thinking ok, at log off clean out / refresh the contents of the home folder so the passwords are no longer there? change permissions on the folders within the home dir - key is to wipe the passwords, this is the crucial bit......

I am going around in circles trying to find a solution to posts that are very old and no longer apply.

Can anyone give me some pointers it would be very much appreciated. Thank you.

---

### Post by The Cog on 2024-07-13
What you are looking for is called **Kiosk Mode**. I know it can be done, but I don't know how. But **Linux Kiosk Mode** is the term you need to search for.

---

### Post by grahammechanical on 2024-07-13
Pardon me, but I think that Kiosk Mode refers to using Ubuntu to power a smart display.

[https://mir-server.io/docs/make-a-secure-ubuntu-web-kiosk?_gl=1*2j8t5k*_gcl_au*MTU4NDQwNzUwNC4xNzE2ODQ2NDQ4](https://mir-server.io/docs/make-a-secure-ubuntu-web-kiosk?_gl=1*2j8t5k*_gcl_au*MTU4NDQwNzUwNC4xNzE2ODQ2NDQ4)

It is also my understanding that the Ubuntu Guest account is no longer available. Not with the default Wayland compositor driving the display. This is why LightDM has to be used.

Here is a more recent guide from early 2023:

[https://www.zdnet.com/article/how-to-add-the-guest-session-feature-in-ubuntu-desktop/#google_vignette](https://www.zdnet.com/article/how-to-add-the-guest-session-feature-in-ubuntu-desktop/#google_vignette)

Regards

---

### Post by TheFu on 2024-07-13
I wouldn't use Ubuntu for this.  More and more Ubuntu is pushing something called snap packages which run in a restricted container that doesn't allow access to the whole file system or even /tmp/.

I'd use a minimal Linux and run it in Kiosk mode. Something like **Tiny Core Linux**.  Don't let anything be written to the disk after boot and no credentials will be shared.  Train people to reboot the computer when they leave for the day and in 15 seconds, a 100% fresh Linux will be back.

---

### Post by seanhaynes1 on 2024-07-14
thank you I'll have a look, much appreciated

---

### Post by seanhaynes1 on 2024-07-14
I was looking at this, thank you.

---

### Post by seanhaynes1 on 2024-07-14
Ok, as grahammechanical suggested I managed to get Lightdm working in a way I needed.

I had tried Lightdm but the problem was the any snap browser wouldn't work..............so the process is too remove snap firefox and install a deb firefox package from the mozillateam ppa.

As of today this works:

[https://www.zdnet.com/article/how-to-add-the-guest-session-feature-in-ubuntu-desktop/](https://www.zdnet.com/article/how-to-add-the-guest-session-feature-in-ubuntu-desktop/)        to install Lightdm and setup a guest account


[https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/](https://ubuntuhandbook.org/index.php/2022/04/install-firefox-deb-ubuntu-22-04/)                  to remove the snap firefox and install a deb version


Tested working, a guest can logon , input credentials, save credentials, log off, log back on and credentials are not saved!

Very pleased thank you for the pointers.

---

### Post by TheFu on 2024-07-14
> **seanhaynes1 said:**
> 
Tested working, a guest can logon , input credentials, save credentials, log off, log back on and credentials are not saved!

Very pleased thank you for the pointers.

If you run a non-Snap constrained browser, please run it inside some sort of protected environment like a container or a jail, so you don't have the trust the browser alone for doing what you seek.  I use **firejail** with the "private" setting, so nothing from the browser ever touches the storage of the computer.  I also use Firefox-ESR to avoid snaps.  The snap is too constraining for my needs.

The command that gets run is this:
```
/usr/bin/firejail --join-or-start=ffNormal --dns=172.22.22.80 \
         --private --rlimit-as=4096000000   \
         /usr/bin/firefox-esr -no-remote  $@ &

```

Firefox will try to use the Mozilla DNS of you don't specifically tell it not to.  Whether that is a good idea or not, depends on your needs. I want to use DNS that I run myself.  I also want to limit the amount of RAM that firefox can see. Above, it is 4GB, but because it is a "private" container, I generally use it for less than an hour each time and RAM doesn't run out. When I need to use it longer, I've made the limit 9GB, which works well for about a week.  The -no-remote isn't needed for most people, so you can remove that, if you like.

Some sort of protection is needed these days for all modern browsers, especially if they allow webRTC, javascript, HTML5 "local objects", and other complex security related choices.  I feel that the complexity of all big browsers make the makers of those browsers highly unlikely to have 100% working, non-buggy, releases.  Bugs means hacking is possible in the best situations.  With Firejail, I've added constraints that are under my control to limit the damage possible when a browser with a bug fails in a bad way.

---

### Post by currentshaft on 2024-07-14
> **TheFu said:**
> 
Some sort of protection is needed these days for all modern browsers, especially if they allow webRTC, javascript, HTML5 "local objects", and other complex security related choices.  I feel that the complexity of all big browsers make the makers of those browsers highly unlikely to have 100% working, non-buggy, releases.  Bugs means hacking is possible in the best situations.  With Firejail, I've added constraints that are under my control to limit the damage possible when a browser with a bug fails in a bad way.

Running the most dangerous piece of software (a web browser) through a setuid binary (firejail) is a sure way to escalate vulnerabilites from bad to horrific. 

[https://seclists.org/oss-sec/2022/q2/188](https://seclists.org/oss-sec/2022/q2/188)

2022-05-03: I contacted the upstream security contact with the
            vulnerability details and offered coordinated disclosure.
2022-05-13: There have been technical problems reaching the security
            contact by email, by creating a GitHub issue we've been able
            to get the attention of the upstream developer team and
            finally to forward the vulnerability details.
2022-05-30: The upstream developers and myself started reviewing the
            first version of the bugfix.

Ten days to even find the developers to contact about a critical CVE, then another two weeks to start working on it.

But let's give this this thing full root access to our systems. Linux security in a nutshell.

---

### Post by TheFu on 2024-07-14
> **currentshaft said:**
>  But let's give this this thing full root access to our systems. Linux security in a nutshell.

And what is the likelihood for the flaw to be used? Seems like it isn't a remote exploit.  Also, I don't allow end-users to mount things on my systems.  The power to mount is the power to destroy.  I've been saying that to Linux people over 20 yrs.  I get that I'm odd.  the only time I allow mounts to happen automatically is through **autofs** - yet another root-running tool.

If you want role-based administration, there are options, just not Debian or Ubuntu. Everyone has different risk factors to consider.

The fix was released 2 yrs ago, after a little over 1 month.  Compare that to fixes from lots of projects and it is very fast.  Compared to MSFT security fixes, this fix moved at light-speed.

---

### Post by #&amp;thj^% on 2024-07-14
After 15 years on running firejail, never ever had any issues.
```
less /etc/firejail/firejail.config|grep force
# force-nonewprivs no
force-nonewprivs yes

```
I run in some Dev circles and they all report no issues currently.

Code is Code>>>Hack, Hash yada yada.

---

### Post by currentshaft on 2024-07-16
> **1fallen said:**
> After 15 years on running firejail, never ever had any issues.

I run in some Dev circles and they all report no issues currently.


If first-hand anecdotal evidence is the only basis for evaluating security posture, there is guaranteed to be eventual surprise and disappointment.

---

