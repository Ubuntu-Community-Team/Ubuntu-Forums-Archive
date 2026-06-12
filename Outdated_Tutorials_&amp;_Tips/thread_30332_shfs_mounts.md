---
title: "shfs mounts"
date: 2005-04-28
forum: Outdated Tutorials &amp; Tips
---

### Post by flurdy on 2005-04-28
Mini mini howto on how to set up a ssh file system

I followed a guide to install shfs, [http://www.ma.utexas.edu/users/stirling/computergeek/lufs.html](http://www.ma.utexas.edu/users/stirling/computergeek/lufs.html) by Spencer Stirling, and it worked straight away in ubuntu( as it was based on debian). 

The only step I had to do was to manually do 'chmod a+s /usr/bin/shfs*' to set the SUID element, so any user can mount folders.

This enables me to mount other machines as folders over ssh.

Simple command like this are now available

shfsmount *machinename*:*/path/to/remote/folder*  */path/to/local/folder*

or just 
shfsmount *machinename*  */path/to/local/folder*
to mount your home directory.

However I was wondering if anyone knows how and where to automaticly mount some of these?

Presume fstab is too early to mount them, so would it have to be in your user profile? Or a a late rcx.d service to mount/unmount them

---

### Post by hod139 on 2005-07-27
I know it has been a while (almost 3 months), but I just stumbled onto this post today, According to [this site](http://www.esat.kuleuven.ac.be/~decockd/wiki/bin/view.cgi/Main/ConfiguringSecureShellFileSystemTOC)  you can use fstab to automount.

add the following In  /etc/fstab:
userid@remoteMachine:/remoteDirectory   /home/userid/remoteDirectory shfs       rw,user,noauto     0       0

However, I can't seem to get shfsmount to work unless I use sudo.  I tried to do a 'chmod a+s /usr/bin/shfs*' but that doesn't work.  Any ideas?

---

### Post by arjay1 on 2005-07-30
Hi - wish I could help you but I have what I presume is a similar problem.  I have managed to get the network drive's folder that I want from another machine, mounted in my home directory on this machine.  But when I mounted it I got:

[I]The authenticity of host '192.168.1.3 (192.168.1.3)' can't be established.
RSA key fingerprint is 27:1a:46:ab:cd:b8:23:2d:db:46:24:be:35:15:a2:aa.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added '192.168.1.3' (RSA) to the list of known hosts.[/I]

The ip address 192.168.1.3 is the other machine. Can you help me with info about where shfs would have written this info (i.e. where the list of known hosts is kept)?

Also, I have what I presume is a similar problem to you in that I can only open the mounted folder if I sudo konqueror to get to it - otherwise it reports that I don't have sufficinet permissions to open the folder.  Even then I can't open certain files - for example, I need to modify an *.ini file but when I open it in a text editor it shows a blank page.  It isn't blank as I can verify by walking down into the basement and viewing the file on the other machine.

I presume this is because the chmod statement is not working.  Any ideas, or have you solved your problem?

---

### Post by hod139 on 2005-07-30
I can aswer your first question, and you are correct that your second problem is the same as mine, and no I still can't get it to work with user rights.

The known hosts are stored in ~/.ssh/known_hosts

---

### Post by varunus on 2005-07-30
Stupid question, but did you make sure to do "sudo chmod a+s /usr/bin/shfs*"?  Otherwise, it won't work; you need to set shfs to have a userid of ROOT, not your user.

---

### Post by hod139 on 2005-07-30
[QUOTE=varunus]Stupid question, but did you make sure to do "sudo chmod a+s /usr/bin/shfs*"?  Otherwise, it won't work; you need to set shfs to have a userid of ROOT, not your user.[/QUOTE]

Yeah, sorry for not being clear.  Here is some terminal output, maybe that will help you know exactly what I have tried, and someone can help me further.
```
 sberard@ent:~$ shfsmount muse:/home/sberard /media/rpishare/
shfsmount: /media/rpishare: Operation not permitted
sberard@ent:~$ sudo chmod a+s /usr/bin/shfs*
sberard@ent:~$ shfsmount muse:/home/sberard /media/rpishare/
shfsmount: /media/rpishare: Operation not permitted
sberard@ent:~$ sudo shfsmount sberard@muse:/home/sberard /media/rpishare/
Password:
sberard@ent:~$ cd /media/rpishare/
-bash: cd: /media/rpishare/: Permission denied
sberard@ent:~$ sudo cd /media/rpishare/
sudo: cd: command not found
sberard@ent:~$ sudo su
root@ent:/home/sberard # cd /media/rpishare/
root@ent:/media/rpishare # 
```

---

### Post by arjay1 on 2005-07-30
varunus - yup i did sudo the chmod.  However, just a question - can I set shfs to allow a user to mount the network drive folders? (BTW I have no idea what the a+s means in the chmod command.)

---

### Post by varunus on 2005-07-30
hod and arjay,

I see both of your problems.  shfsmount is set to let you mount as a user, but you're trying to mount to a directory owned by root (/media/rpishare for you hod).

So, after doing that chmod, shfsmount is correctly set.  Try doing the following as your normal user.
```

cd ~
mkdir sword
shfsmount login@server ~/sword/
```

It should work.

---

### Post by arjay1 on 2005-07-30
varunus - hope I did what you meant me to do:

rjoss@dell1:~$ cd /home/rjoss
rjoss@dell1:~$ mkdir sword
rjoss@dell1:~$ shfsmount rjoss@dell1 /home/rjoss/sword
ssh: connect to host dell1 port 22: Connection refused

(I did check that the sword dir had been created)

EDIT: BTW - doesn't work even if I sudo shfsmount ..

Get the same error message

---

### Post by varunus on 2005-07-30
arjay,

That looks like an ssh problem, not a shfsmount problem.  Try regular ssh; I'm pretty sure it'll fail in that case, the dell is rejecting your connection.

EDIT: Typos

---

### Post by arjay1 on 2005-07-31
varunus - thanks for trying anyway.  When you say "use regular ssh" - what exactly do you mean?

---

### Post by hod139 on 2005-07-31
[QUOTE=varunus]hod and arjay,

I see both of your problems. shfsmount is set to let you mount as a user, but you're trying to mount to a directory owned by root (/media/rpishare for you hod).
[/QUOTE]

Varunus, thanks for your reply.  I can mount a folder owned by myself, but I thought the point of setting the shfsmount command to root (sudo chmod a+s /usr/bin/shfs*)  was so it could mount a folder owned by root.  What would I do to allow 
```
sberard@ent:~$ shfsmount muse:/home/sberard /media/rpishare/
```
to mount, where /media/rpishare is owned by root?

I suppose this isn't a big deal, since I'm using fstab to automount at startup, but I will still like to know why it isn't mounting a folder owned by root.

arjay1,
Varunus means just try connecting to the machine using ssh:
```
ssh rjoss@dell1
```
If that fails, then that is why shfsmount is failing.  Make sure you have the machine name correct, and and ssh server is running on it.

---

### Post by arjay1 on 2005-08-01
Hod139 -thanks for the advice re ssh.  I tried "ssh rjoss@dell1" as you suggested and got it eventually.  This is the terminal output:

[I]rjoss@dell1:~$ ssh rjoss@dell1
The authenticity of host 'dell1 (127.0.0.1)' can't be established.
RSA key fingerprint is 2a:b8:05:df:37:14:72:77:46:4c:b4:41:03:13:79:10.
Are you sure you want to continue connecting (yes/no)? y
Please type 'yes' or 'no': yes
Warning: Permanently added 'dell1' (RSA) to the list of known hosts.
Password:
Linux dell1 2.6.10-5-386 #1 Fri Jun 24 16:53:01 UTC 2005 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have new mail.
Last login: Sun Jul 31 19:33:57 2005
rjoss@dell1:~$[/I]

Presumably that means it worked?

---

### Post by hod139 on 2005-08-01
So, it looks like you are ssh'ing to your own machine (127.0.0.1).  If shfsmount still doesn't work, maybe it is because shfsmount is smart enough to not mount a local file system as remote.  Also, why would you want to shfsmount a local file system?

---

### Post by arjay1 on 2005-08-01
**I** didn't want to mount a local filesystem - I was responding to your comment that Varunus meant I should "ssh rjoss@dell1"  which is what I tried!

I have now tried to ssh another computer on the network - see below.  It is interesting that if I use the machine's name - rjoss@rjoss it says name or service not known.  But if I substitute the ip address for the name it seems to work OK:

"root@dell1:~# ssh rjoss@rjoss
ssh: rjoss: Name or service not known


root@dell1:~# ssh rjoss@192.168.1.3
Password:
Linux rjoss 2.6.10-5-686-smp #1 SMP Fri Jun 24 18:12:58 UTC 2005 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.
You have new mail.
Last login: Sun Jul 31 19:26:01 2005
rjoss@rjoss:~$

---

### Post by hod139 on 2005-08-01
If dell1 is on the same network as rjoss, then it is surprising that you need to type the ip address.   If they are not on the same network, then that is why you cannot connect, you need the full address. 

Does shfsmount work if you use the ip address?

---

### Post by arjay1 on 2005-08-02
[QUOTE=hod139]If dell1 is on the same network as rjoss, then it is surprising that you need to type the ip address.   If they are not on the same network, then that is why you cannot connect, you need the full address. 

Does shfsmount work if you use the ip address?[/QUOTE]

Yup - they are both on the same (only) network and both are running kubuntu.  Also, shfs will not id the computer if I use its name, but will id it ok if I use the ip address.

---

### Post by flurdy on 2005-08-03
[QUOTE=arjay1]Yup - they are both on the same (only) network and both are running kubuntu.  Also, shfs will not id the computer if I use its name, but will id it ok if I use the ip address.[/QUOTE]

Surely, unless you have local dns server, you need to add these other machines to you hosts file?
Otherwise how will you machine know what ip machine rjoss is ?

---

### Post by arjay1 on 2005-08-03
Take your word for it - I am only a newbie and boy is this new territory for an old windows hand.

Anyway - can you give some advice about how to add them to the hosts file?  TIA

---

### Post by Flane on 2005-08-08
Hi,

i've tried it and done as described in the howto.
After patching the lufs source everything worked well and i installed the module and was also able to do

sudo modprobe lufs

but unfortunately the sshfs which i need isn't included in the lufs-utils package from universe. So lufsmount sshfs://.. doesn't work.

Where can i get the correct lufs-utils package with ssfs?

Thanks
Flane

---

### Post by flurdy on 2005-08-09
[QUOTE=arjay1]Take your word for it - I am only a newbie and boy is this new territory for an old windows hand.

Anyway - can you give some advice about how to add them to the hosts file?  TIA[/QUOTE]

sudo vi /etc/hosts


then add lines like these at the end:

192.168.0.10          kermit.domain.com     kermit
192.168.0.20         piggy.domain.com     piggy

if the machine  names are kermit and piggy.

---

### Post by arjay1 on 2005-08-09
flurdy - brilliant pal - just what I needed.

BTW I have dropped kubuntu and ubuntu in favour of debian, proper.  I just had too many problems - flakey KDE; lock ups and others too many and varied to mention - even more problems when i opened up the wider repos (I found the basic ones too restrictive).  :mad: 

Any way I am now a fully fledged debian and happy as a bunny (at the moment  - watch this space)  \\:D/

---

### Post by syrus on 2005-10-11
Right then, I've been having some very abnormal problems with using SHFS and Ubuntu Breezy badger.

Basically, the problem lies in installing the kernel module that is built by module-assistant, if I follow the usual apt-get and module-assistant guide, everything works as expected until I try to either unmount an SHFS mount or delete a file from an SHFS mount. I get the following in my dmesg output:

[4295251.517000] SHell File System, (c) 2002-2004 Miroslav Spousta
[4295329.623000] ------------[ cut here ]------------
[4295329.623000] kernel BUG at <bad filename>:33675!
[4295329.623000] invalid operand: 0000 [#1]
[4295329.623000] Modules linked in: shfs rfcomm l2cap bluetooth cpufreq_powersave cpufreq_stats cpufreq_userspace cpufreq_ondemand cpufreq_conservative freq_table pcmcia i915 drm tc1100_wmi video battery ibm_acpi container i2c_acpi_ec i2c_core button pcc_acpi sony_acpi ac dev_acpi hotkey ipv6 af_packet rtc pcspkr ipw2200 firmware_class ieee80211 ieee80211_crypt yenta_socket rsrc_nonstatic pcmcia_core snd_intel8x0 snd_ac97_codec snd_pcm_oss snd_mixer_oss snd_pcm snd_timer snd soundcore snd_page_alloc tpm_nsc tpm_atmel tpm shpchp pci_hotplug hw_random intel_agp agpgart dm_mod tsdev evdev psmouse mousedev parport_pc lp parport md reiserfs thermal processor fan e100 mii ehci_hcd uhci_hcd usbcore ide_cd cdrom ide_disk ide_generic piix ide_core unix vesafb capability commoncap vga16fb vgastate softcursor cfbimgblt cfbfillrect cfbcopyarea fbcon tileblit font bitblit
[4295329.623000] CPU:    0
[4295329.623000] EIP:    0060:[<c0158658>]    Not tainted VLI
[4295329.623000] EFLAGS: 00210202   (2.6.12-9-386)
[4295329.623000] EIP is at clear_inode+0x16/0xd2
[4295329.623000] eax: d8f26e5c   ebx: d8f26e5c   ecx: d8f26e5c   edx: d8f26e5c
[4295329.623000] esi: f060f974   edi: 00000001   ebp: d353e000   esp: d353fef8
[4295329.623000] ds: 007b   es: 007b   ss: 0068
[4295329.623000] Process umount (pid: 9759, threadinfo=d353e000 task=d0e3f520)
[4295329.623000] Stack: d8f26e5c f060f974 c01591d3 d8f26e5c d0d7ca6c d8f26e5c c0157374 d8f26e5c
[4295329.623000]        d082284c d082284c f0617860 c01575c7 0000001a d7b3d000 c0149af9 d082284c
[4295329.623000]        00000010 f06178c0 08050271 c014a0cc d7b3d000 d7b3d000 c0149a82 d7b3d000
[4295329.623000] Call Trace:
[4295329.623000]  [<f060f974>] shfs_delete_inode+0x0/0xe2 [shfs]
[4295329.623000]  [<c01591d3>] generic_delete_inode+0x97/0xef
[4295329.623000]  [<c0157374>] prune_dcache+0x129/0x149
[4295329.623000]  [<c01575c7>] shrink_dcache_parent+0xd/0x1b
[4295329.623000]  [<c0149af9>] generic_shutdown_super+0x1e/0xca
[4295329.623000]  [<c014a0cc>] kill_anon_super+0xe/0x25
[4295329.623000]  [<c0149a82>] deactivate_super+0x26/0x39
[4295329.623000]  [<c015a9e7>] sys_umount+0x66/0x6e
[4295329.623000]  [<c015a9fa>] sys_oldumount+0xb/0xe
[4295329.623000]  [<c0102e9f>] sysenter_past_esp+0x54/0x75
[4295329.623000] Code: c7 42 04 24 1a 2a c0 89 15 24 1a 2a c0 ff 0d c8 7a 37 c0 5b c3 56 53 8b 5c 24 0c 53 e8 9a e0 fe ff 83 bb c8 00 00 00 00 58 74 02 <0f> 0b 8b 83 2c 01 00 00 a8 10 75 02 0f 0b a8 20 74 02 0f 0b 8b
[4295329.623000]

(The first line is where I've modprobe'd shfs)

During the module-assistant install shfs, I did get an error saying it couldn't find gcc-3.4, so I apt-got that and it built fine....I have the feeling the problem is something to do with the kernel being built with gcc-3.3 although I'm not entirely sure about that.

I get the feeling this will be a common problem for users of Breezy badger as I didn't do anything weird and I'm using the stock kernel:
Linux feeg 2.6.12-9-386 #1 Mon Oct 10 13:14:36 BST 2005 i686 GNU/Linux
on a completely fresh install.

The only repositories I'm using to get things are:
breezy-restricted
breezy-universe

(I think the shfs stuff is in the universe repo)

Thanks in advance anyone who can help me on this one? Like I say, I think it may be the gcc version used to build the module, although I've no idea how to get module-assistan to compile things using the kernel's gcc, perhaps it already is...perhaps it doesn't matter? :confused:

---

### Post by malv on 2005-10-20
Hi Syrus,

I have exactly the same experience. I managed to install shfs through the debian info.

I also tried it in SuSE10.0 with 2.6.13 and gcc4. Here I had to patch shfs with the known patch for gcc4. The experience is identical as with ubuntu 5.10. Everything goes well till you do shfsumount, then you get the same disaster scenario. BTW everything works ok in SuSE9.3.

Comparing the Ubuntu and the identical SuSE behavior, I wonder whether not something went wrong since the 2.6.12 kernel? Maybe shfs needs more rework than the patches now on the web. Maybe the problem resides somewhere in ssh?

malv

---

### Post by timosa on 2005-10-21
I have also same kernel bug problem with the shfs. The module works some hours but then starts to make those same invalid operations as for you. Eventually it seems to corrupt display memory (I have integrated 82845G/GL ). I tried to download and compile the original (non-Debian) version of the shfs but it gave same results. BTW, the default Ubuntu kernel seems to be compiled with gcc-3.4.

---

