---
title: "How to succeed previous environment on and after new ubuntu installation ?"
date: 2020-10-13
forum: New to Ubuntu
---

### Post by nnn1308 on 2020-10-13
When I change ubuntu version from 19 to 20, or  re-install "20.04.1 LTS (Focal Fossa)" again for some reason,
I'm grateful if I could get the utilities to succeed previous environment. (For example,  .bash_aliases,  smb.conf  ...etc.)

You may say, " use upgrade", but I do not want upgrade my unstable version.
I sometimes re-install "20.04.1 LTS (Focal Fossa)" from the first, the "upgrade" is unavailable.

Thanks in advance!!!

---

### Post by guiverc on 2020-10-13
It's best if you're specific with details.

Ubuntu has standard releases which are *year.month* in format, such as Ubuntu 20.04 LTS.

Ubuntu also has specialist releases which use the *year* format, such as Ubuntu Core 20
 (*LTS isn't mentioned with these releases generally; they all have 10 years of supported life so it's actually longer than the LTS for the other products*)

They are different products, and thus you should **not** try to move from a* yy* release to a *yy.mm* release.  This is not probably what you want to do, as there were no *yy* releases in 2019, as they're only released on even years (2016, 2018, 2020 etc)

What release are you using currently?  There is no Ubuntu 19.
Is it a desktop?  server? or something-else?

---

### Post by nnn1308 on 2020-10-13
> [COLOR=#000000] you should [/COLOR][B]not try to move from a[I] yy release to a [I]yy.mm release

Yes, I agree with your opinion,
so, I'm expecting a tool which uses "diff & patch".
If the assist tool shows me the diff results one by one.
I can decide if I may overwrite, or I must edit for myself.

[/I][/I][/B]Desktop:   Ubuntu 19.10 was deleted and I installed [COLOR=#000000] "20.04.1 LTS (Focal Fossa)".

[/COLOR]******

---

### Post by Impavidus on 2020-10-14
19.10 reached end-of-life 3 months ago, so don't use it. Release upgrades from end-of-life releases are often more problematic and so is upgrading a broken system, so don't even try. Make it a fresh install. But I get the impression that you already understood that.

User settings (like your .bash_aliases) are all stored in the /home directory. You can simply keep it and it should work. Easiest if you have a separate /home partition (tell the installer you want to use that partition again as /home and don't format it, then make sure you use the same username as before and create users in the same order), but you can also keep your /home if you don't have a /home partition. You can restore from a backup or try a dirty install.

System settings (like your smb.conf) are in /etc. Don't restore all of your old /etc to the new system. It will break it. Instead, just backup the files you changed and integrate them back into the system after the install. Be careful, sometimes things change. diff can show you the differences, but it takes a brain to decide whether you can simply overwrite or have to integrate things.

---

### Post by grahammechanical on 2020-10-14
I am not completely sure of what you want to do.

If we have /home on the same partition as / then everything in our home folder is wiped out if we format that partition during a reinstallation. We could refuse to format the partition and hope for the best. But various libraries and configuration files will be over written anyway.

If we have /home on its own partition and do not allow the reinstallation process to format  the /home partition then our application configuratation files will not be lost and the reinstalled applications will use the existing configuration files.

An official upgrade from one version of Ubuntu to the next will preserve the configurations files in /home whether /home is in the same partition as / or in its own partition.

Regards

---

### Post by ActionParsnip on 2020-10-14
Just keep backups of the files you want to keep. When you reinstall, just restore the files

---

### Post by TheFu on 2020-10-14
> **ActionParsnip said:**
> Just keep backups of the files you want to keep. When you reinstall, just restore the files

I agree.

I think the OP wants a magical way for prior system settings to be carried forward from old install to fresh install.  The bad news is there is no magic, short of having backups.  When a fresh install happens, a fresh install happens. Not choosing to format the storage and just install new programs over the old will likely result in an unstable system, as the OP currently has.  Wipe and completely pave over is the fix for that problem.

And having backups with any files we want to retain. Then we can put those file back where they belong post-install.

---

### Post by nnn1308 on 2020-10-14
Thanks for your comment.
The /home is easy to backup /restore.
But, how I restore my setting in /etc, /usr/lib ...etc.

Currently, I always keep "what I did" on my /mnt/otherdisk/MyUbuntHistory.txt
and I install several applications one by one according the records.

Maybe, I should keep my diary from "#!/bin/sh" everyday.  :)

---

### Post by guiverc on 2020-10-14
> **nnn1308 said:**
> > [COLOR=#000000] you should [/COLOR]not try to move from a[I] yy release to a [I]yy.mm release

Yes, I agree with your opinion,
so, I'm expecting a tool which uses "diff & patch".
If the assist tool shows me the diff results one by one.
I can decide if I may overwrite, or I must edit for myself.[/I][/I]Desktop:   Ubuntu 19.10 was deleted and I installed [COLOR=#000000] "20.04.1 LTS (Focal Fossa)".

[/COLOR]

My statement related to Ubuntu's releases in the format *yy* such as 
- Ubuntu Core 18

which are different to standard releases using the format *yy.mm* such as
- Ubuntu 18.04 LTS Server

They are different products, and Ubuntu Core 18 should be upgraded to Ubuntu Core 20, not attempted to upgrade to the different product of Ubuntu 20.04 LTS.

Ubuntu Core 18 is closest to the server product range (18.04), however it's still different. If you install for example the GNOME desktop on the 18.04 Server, it'll installed as *deb* packages and run natively. On Ubuntu Core 18 however it'll install and run as a *snap* running in a containerized environment.  The *yy* releases differ to *yy.mm* releases.

Ubuntu Core 18 should be upgraded to Ubuntu Core 20.
Ubuntu 18.04 LTS should be upgraded to Ubuntu 20.04 LTS.

---

### Post by nnn1308 on 2020-10-15
Thank you for your comment.
Now, I no longer have 18.04 or 19.10, I only have "20.04.1 LTS (Focal Fossa)".

In future, I'm happy if I can get my previous environment like,
$ cat [COLOR=#000000] /mnt/otherdisk/MyUbuntHistory.txt | sudo /bin/sh[/COLOR]

---

### Post by TheFu on 2020-10-15
> **nnn1308 said:**
>  
In future, I'm happy if I can get my previous environment like,
$ cat [COLOR=#000000] /mnt/otherdisk/MyUbuntHistory.txt | sudo /bin/sh[/COLOR]

That would be extremely dangerous. Every system is a little different. Minimally, each has different UUIDs for storage, different device names for ethernet devices, and as we learn more, we'll setup things a little different.

There is no magic.  Blindly running commands that aren't 100% known to be safe is foolish.

There are some options, but it depends on your skills.

If you work in IT, perhaps you'd setup Ansible playbooks for each setup task. These are repeatable, but hardly worth the effort for 1-3 systems in a home environment.  I use Ansible to setup my base server installs.  Some weeks, it feels like my job is maintaining ansible configurations.

If you are a typical end-user or in a small environment, just be certain to add a unique, consistent comment to any files you touch under /etc/. Then you can **grep** for that tag/comment during restore time.  I backup everything under /etc/ because it is full of very useful information, but when it comes time to restore, I'm extremely selective about which files need to be copied and which files need to be manually edited back onto the new system. A good starting point would be to find all files that have been touched since the date you installed the OS under /etc/.  The 'find' command can do that.  I think it is easier just to keep a tag/comment in each file to be searched later.

There isn't any magic. Sorry.

---

### Post by nnn1308 on 2020-10-15
#!/bin/sh
# [COLOR=#000000]/mnt/otherdisk/MyUbuntHistory.txt [/COLOR]
VT=f2
SPEED=155

MSG=`
cat <<'_END_'  ;
That would be extremely dangerous. Every system is a little different. Minimally,
each has different UUIDs for storage, different device names for ethernet devices,
and as we learn more, we'll setup things a little different.
...blah blah blah....
There isn't any magic. Sorry.
_END_
`

echo $MSG
xcowsay "$MSG" &
espeak -s $SPEED -v $VT  "$MSG"


AKS=
YES=
NO=
ask()
{
        echo ""
        echo -n "$ASK (y/n): "
        read ans
        case $ans in
        y*) echo "okay! $YES" ;;
        *) echo "$NO"  ;exit ;;
        esac
}

ASK='Continue??'
NO='good boy!'
ask

---

### Post by metacell on 2020-10-16
I agree with previous speakers. There's no simple way to transfer your settings to a new installation. You have to find a method that works for each application.

For example, if you find yourself copy/pasting lines like 

```
sudo add-apt-repository ppa:lutris-team/
sudo apt update
sudo apt install lutris
```

to setup all your applications when you install Ubuntu, you can put them in a script file instead. Eg,

```
sudo add-apt-repository ppa:aaa
sudo add-apt-repository ppa:bbb
sudo add-apt-repository ppa:ccc
sudo apt update
sudo apt install aaa bbb ccc
```

You may still need to edit the script when a PPA or your Ubuntu version changes.

---

### Post by nnn1308 on 2020-10-16
Nice idea !!!

---

