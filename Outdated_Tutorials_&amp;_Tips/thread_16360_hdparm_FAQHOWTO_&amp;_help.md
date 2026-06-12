---
title: "hdparm FAQ/HOWTO &amp; help"
date: 2005-02-21
forum: Outdated Tutorials &amp; Tips
---

### Post by wallijonn on 2005-02-21
From [http://www.ubuntuforums.org/showthread.php?t=10250&page=3&pp=10&highlight=hdparm](http://www.ubuntuforums.org/showthread.php?t=10250&page=3&pp=10&highlight=hdparm) :
----------------------------------------------------------------------------------------------------------------------------------

let's say that you open up a Root Terminal and issue the [COLOR=Red]hdparm[/COLOR] command:
```

hdparm -h

```
You should see a list of commands that you can issue.

The first two commands that you want to look at are
```

hdparm -i /dev/hda
hdparm -I /dev/hda
hdparm -i /dev/hda1
hdparm -I /dev/hda1

```

Now let's day that your dma is set to off and you wish to set it to on. Then you'd ```
hdparm -d1 /dev/hda
```
But if you wish to make it so that that setting is set during bootup, you know that we will have to [COLOR=Red]gedit /etc/hdparm.conf[/COLOR].

So, open up a Root Terminal, cd over to /etc and [COLOR=Red]sudo gedit hdparm.conf[/COLOR]
Go to the end of the file and highlight & copy 
```

#/dev/hda {
#	mult_sect_io = 16
#	write_cache = off
#	dma = on
#}

```
Now right click / paste it at the very end of the file (after starting a new line after hitting carriage return).

Now remove the # from the front of all those new lines you've copied from the end of YOUR file.

**This is where you'll be making all your changes**.

You would first make sure that your setting a command in the Root Terminal will work. 

So let's say that when I did a hdparm /dev/hda command I got back
```

/dev/hda:
 multcount    =  0 (off)
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 using_dma    =  0 (off)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 58168/16/63, sectors = 58633344, start = 0

```
So I give this command [COLOR=Red]hdparm -d1 -m1 /dev/hda[/COLOR]
Now when I [COLOR=Red]hdparm /dev/hda[/COLOR] I get 
```

/dev/hda:
 setting multcount to 1
 multcount    =  1 (on)
 setting dma to 1
 dma = 1 (on)

```
So I would now modify my [COLOR=Blue]hdparm.conf[/COLOR] to read
```

/dev/hda {
	mult_sect_io = 32
	dma = on
}

```
save it and reboot.

Please note that these are commands in a mock up. In no way do I endorse your putting in [COLOR=Red]mult_sect_io = 32[/COLOR] if your HD cannot support it. The same would go for all the other commands.

Since all you want to do is set DMA, you'd 
```
[color=red]
/dev/hda {
	dma = on
}
[/color]
```
<save, reboot>

But before rebooting I would [COLOR=Red]hdparm /dev/hda[/COLOR]. This is what it looks like now (after issuing an [COLOR=Red]hdparm -c1 -d1 -m1 /dev/hda[/COLOR] command:
```

/dev/hda:
 multcount    =  1 (on)
 IO_support   =  1 (32-bit)
 unmaskirq    =  0 (off)
 using_dma    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)
 geometry     = 58168/16/63, sectors = 58633344, start = 0

```
You should see some new messages regarding hdparm when it is booting up.

Just be careful when playing around with the ATA settings. The numbers don't quite go the way you'd expect. 

Now, you'll want to test all your settings before ever touching /etc/hdparm.conf.
The commands to do that are:
```

hdparm -t /dev/hda
hdparm -T /dev/hda

```
But just testing /dev/hda is really testing just the channel and not the drive itself.

So you should really be saying
```

hdparm -t /dev/hda1
hdparm -T /dev/hda1

```
for example.

(I think this _may_ work. I've never had to use it to set individual drive settings. And I doubt that you could turn on DMA for just one drive on a chain as the DMA setting affects the controller which will in turn affect each individual drive. But it may give you different test results when testing a drive; at least it did me.) 
```

/dev/hda1 {
	dma = on
}

```

So my advice is:

Issue a 'set' command in a Root Terminal.
Run a -i, -I, -t and -T test.
Only then commit the changes to [COLOR=Blue]/etc/hdparm.con[/COLOR]f and reboot.

As always, _it is best if you make a backup of all your precious data onto a CDR before making radical changes_. And always have your Ubuntu Live CD at the ready.

From /etc/hdparm.conf:
[size=4][COLOR=RED]Note that if the init script causes boot problems, you can pass 'nohdparm'  on the kernel command line, and the script will not be run.[/COLOR][/size]

---

