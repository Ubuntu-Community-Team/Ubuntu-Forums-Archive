---
title: "Newbie's (pun intended) guide to HDAPS disk protection"
date: 2007-08-26
forum: Outdated Tutorials &amp; Tips
---

### Post by gnyffel on 2007-08-26
This guide is a rather simple guide to enable the disk protection feature in some Thinkpad laptops under (K,X)Ubuntu 7.04. I will not be held responsible if you mess up your rig following this guide, but I'm fairly certain that it won't be. Keep backups, yeah?

This guy has touched on the subject previously, and he links to a rather nice guide:
[http://ubuntuforums.org/showpost.php?p=3168006&postcount=8](http://ubuntuforums.org/showpost.php?p=3168006&postcount=8)

This part is, apart from some clarification, mostly thanks to this guy:
[http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_on_a_ThinkPad_T43#Active_Protection_System_.28acceleration_monitor.29](http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_on_a_ThinkPad_T43#Active_Protection_System_.28acceleration_monitor.29)

(Got a 3945ABG wireless card? Skip this and read "The easy way" instead)

**Preparing the kernel**

Needed files:
```
sudo aptitude install build-essential fakeroot kernel-package libncurses5-dev wget bzip2 linux-source
```

Source package dependencies are extra, and I can't say if you'll need something more for those. You can usually figure it out from ./configure output, though.

First, we'll unpack the kernel source, make a symlink, then apply the hdaps_protect patch.
```
cd /usr/src
sudo su
aptitude install linux-source
tar xjf linux-source-2.6.20.tar.bz2
ln -s /usr/src/linux-source-2.6.20 /usr/src/linux
wget http://cache.gmane.org//gmane/linux/drivers/hdaps/devel/993-001.bin
cd /usr/src/linux
patch -p1 -l < ../993-001.bin
```

Now, if you use restricted drivers for your wireless, you'll need to do the following:
For ipw3945:
Get and install source debs from [_Debian testing_]("http://packages.debian.org/testing/net/ipw3945-source")
```
dpkg -i /path/to/ipw3945-source_1.2.2-1_all.deb
```
Unpack to kernel source
```
tar xjf ipw3945.tar.bz2
```

Upon further reflection, I think it would be wise to follow the same procedure for ipw3945d, but I can't be sure. I've gotten around this by symlinking to the already built ipw3945d. Oh well.

For Atheros chipsets:
Get the source deb from [_Debian testing_]("http://packages.debian.org/testing/net/madwifi-source")
```
dpkg -i /path/to/madwifi-source_0.9.3.3_all.deb
```

The same as above is probably true for madwifi-tools. Anyone care to enlighten me?

Here, we import the configuration file of our current kernel. I'm not entirely certain if
this is necessary (maybe it's already there?), but at worst it is redundant. Hopefully someone replying will know.
```
cp /boot/config-`uname -r` .config
```

Getting ready to compile the kernel:
```
make clean
make oldconfig
fakeroot make-kpkg clean
```

And finally we can start the build process. Note that you can specify a name of your own
choosing instead of hdapscustom. It'll take something around 1-2 hours to complete, depending
on how fast your machine is.
```
fakeroot make-kpkg --append-to-version=.hdapscustom kernel_image --initrd binary
```

Once built, we need to install our new kernel:
```
cd ..
dpkg -i linux-*.deb
```

Notice how it complains about missing firmware? That's because I'm too much of a newbie to know how to do this properly. We'll create a symlink for using the firmware
selection of our previous kernel (which I'll assume to be 2.6.20-16)
```
ln -s /lib/firmware/2.6.20-16-generic /lib/firmware/2.6.20.3-ubuntu1.hdapscustom
```

We update our initramfs (the one that failed to do so before)
```
update-initramfs -u
```

You should now have a functional hdaps_protect-enabled kernel ready to boot. Reboot into the new kernel.
[B]
Enabling disk protection[/B]

In addition to the kernel patches, you'll need tp_smapi (not strictly required, but preferable) and hdaps. Also needed is a daemon to do the actual protection.
Install tp_smapi from source (also replaces hdaps with better version):
[_Download source tarball._]("http://sourceforge.net/project/showfiles.php?group_id=1212&package_id=171579")
```
tar xf tp_smapi-0.32.tgz
cd tp_smapi-0.32
sudo make install HDAPS=1
sudo echo hdaps >> /etc/modules
sudo echo tp_smapi >> /etc/modules
```

Now we need to insert our new modules:
```
sudo modprobe tp_smapi
sudo modprobe hdaps
```

Install hdapsd (available from feisty-backports)
```
sudo aptitude install hdapsd
```

Make udev rule for hdapsd to find the tp_smapi hdaps sysfs interface (courtesy of this guy: :[http://article.gmane.org/gmane.linux.drivers.hdaps.devel/1040):](http://article.gmane.org/gmane.linux.drivers.hdaps.devel/1040):)
```
sudo echo 'KERNEL=="event[0-9]*", ATTRS{phys}=="hdaps/input1", ATTRS{modalias}=="input:b0019v1014p5054e4801-*", SYMLINK+="input/hdaps/accelerometer-event"' > /etc/udev/rules.d/51-hdaps.rules
sudo udevtrigger
```

In case your hard drive isn't /dev/hda (which it most likely isn't in Feisty - something about an old IDE driver being replaced in the kernel?), you'll need to edit /etc/default/hdapsd accordingly. Mine says
```
DISK="sda"
```

At this point, you'll have functional disk protection, but most people want a nifty little GUI to tell you it's working as well.

For KDE/Kubuntu, you'll want khdapsmonitor:
```
wget http://roy.marples.name/files/khdapsmonitor-0.1.tar.bz2
tar xjf khdapsmonitor-0.1.tar.bz2
cd khdapsmonitor-0.1
./configure
make
sudo make install
```

For Gnome/Ubuntu (and possibly Xubuntu), you'll want gnome-hdaps-applet
```
mkdir gnome-hdaps-applet
cd gnome-hdaps-applet
wget http://www.zen24593.zen.co.uk/hdaps/gnome-hdaps-applet-20060120.tar.gz
tar xf gnome-hdaps-applet-20060120.tar.gz
gcc $(pkg-config --cflags --libs libpanelapplet-2.0) -o gnome-hdaps-applet gnome-hdaps-applet.c
sudo cp gnome-hdaps-applet /usr/bin
sudo mkdir /usr/share/pixmaps/gnome-hdaps-applet/
sudo cp *.png /usr/share/pixmaps/gnome-hdaps-applet/
sudo cp GNOME_HDAPS_StatusApplet.server /usr/lib/bonobo/servers/
```

Restart GNOME and you should find the "HDAPS Status" applet in the "Add to Panel" dialog

If you neglected to experiment (successfully) with ipw3945d, it's possible you need to create this symlink (unless your wireless network works, in which case I just messed up):
```
sudo ln -s /sbin/ipw3945d-2.6.20-16-generic /sbin/ipw3945d-2.6.20.3-ubuntu1.hdaps1
```

**The easy way**
Woo. Be lazy, download the precompiled kernel image and skip the whole kernel compilation section :O

I've made a torrent available. Please seed for a bit. It's &#733;280mb, should download faster than compiling it manually. It'll only work with the ipw3945 wireless chipset however, because I hadn't thought as far as to include madwifi drivers as well when I compiled. See the download page for instructions for use.

[http://thepiratebay.org/tor/3785517](http://thepiratebay.org/tor/3785517)

---

### Post by immeëmosol on 2008-06-25
Okay,

it's a pretty good guide for newbies though!   :D

So, no pun taken here.

There were some issues though.
But after some searching I figured it out.
I had to install the development version of the panel library

# aptitude install libpanel-applet2-dev

then add the directory where the .pc file is

# export PKG_CONFIG=/usr/lib/pkgconfig

And then I could run

# gcc $(pkg-config --cflags --libs libpanelapplet-2.0) -o gnome-hdaps-applet gnome-hdaps-applet.c

succesfully.

For the export-command credits go to here:
[http://osdir.com/ml/gnome.apps.bubblemon/2003-02/msg00000.html](http://osdir.com/ml/gnome.apps.bubblemon/2003-02/msg00000.html)

besides that I used the command:

# dpkg -L libpanel-applet2-0
OR
# dpkg -L libpanel-applet2-dev

to see where the .pc files where.

That's all that was notably different from my steps and yours, you already had those files probably.

So, if you add this it's realy newbie-proof I think..

---

### Post by InfinityCircuit on 2008-06-26
Most of this is no longer necessary:

1) git clone git://zen-sources.org/zen/kernel.git hdaps-kernel
2) cd hdaps-kernel
3) make oldconfig && make menuconfig
4) make-kpkg --initrd --rootcmd fakeroot kernel_image
5) aptitude install hdapsd
6) edit /etc/default/hdapsd
7) /etc/init.d/hdapsd restart

Zen sources has all the patches you need for hdaps, in addition to undervolting/wireless/tuxonice.

---

### Post by waterloo2005 on 2008-08-05
i am using 8.04.
when i run  patch -p1 -l < ../993-001.bin ,
I get the message:
patch unexpectedly ends in middle of line
patch: **** Only garbage was found in the patch input.

How to conquer it?
Thanks

---

### Post by InfinityCircuit on 2008-08-05
For Hardy Heron, you need 2.6.24-rc3 patches + the libata fix:

[http://article.gmane.org/gmane.linux.drivers.hdaps.devel/1094](http://article.gmane.org/gmane.linux.drivers.hdaps.devel/1094)
[http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2008-February/042226.html](http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2008-February/042226.html)

By the way, gnome-hdaps-applet is now in my PPA ([https://launchpad.net/~dmoerner/+archive](https://launchpad.net/~dmoerner/+archive))

---

### Post by waterloo2005 on 2008-08-05
> **InfinityCircuit said:**
> For Hardy Heron, you need 2.6.24-rc3 patches + the libata fix:

[http://article.gmane.org/gmane.linux.drivers.hdaps.devel/1094](http://article.gmane.org/gmane.linux.drivers.hdaps.devel/1094)
[http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2008-February/042226.html](http://mailman.linux-thinkpad.org/pipermail/linux-thinkpad/2008-February/042226.html)

By the way, gnome-hdaps-applet is now in my PPA ([https://launchpad.net/~dmoerner/+archive](https://launchpad.net/~dmoerner/+archive))

Yes,I am using 2.6.24.

which patch should I use?

I should copy the codes in above two web pages?

Thanks a lot!

---

### Post by InfinityCircuit on 2008-08-05
Use both of the above patches from the root of the kernel source directory.  The patches were created with diff -Prun and are delineated by the first set of hyphens "---".

---

### Post by sotirisp on 2008-08-07
infinity can you please give me some help on this?
I try to follow your directions in order to enable APS support for my **Hardy Heron 2.6.24-19-generic**.

_First thing to ask:_

The 2 patches you provided should be applied **BEFORE** or **AFTER** the steps numbered 1),2)...7) ??

_Second thing:_

Step 3): "make oldconfig && make menuconfig" gives a big output with questions to be answered* with a "Yes/No/?" .

What should i answer to all these questions?

I am new at this... :(

EDIT: ..Also another question, those 2 patches should be applied to the **/hdaps-kernel** directory or to the **/usr/src/linux-source-2.6.24** directory ?

---

### Post by sotirisp on 2008-08-07
> **sotirisp said:**
> infinity can you please give me some help on this?
I try to follow your directions in order to enable APS support for my **Hardy Heron 2.6.24-19-generic**.

_First thing to ask:_

The 2 patches you provided should be applied **BEFORE** or **AFTER** the steps numbered 1),2)...7) ??

_Second thing:_

Step 3): "make oldconfig && make menuconfig" gives a big output with questions to be answered* with a "Yes/No/?" .

What should i answer to all these questions?

I am new at this... :(

EDIT: ..Also another question, those 2 patches should be applied to the **/hdaps-kernel** directory or to the **/usr/src/linux-source-2.6.24** directory ?

bump -> i need a help on this someone...

---

### Post by InfinityCircuit on 2008-08-08
I live to serve...:lolflag:

Try this:

sudo apt-get build-dep linux-image-$(uname -r)
sudo apt-get install fakeroot
apt-get source linux-image-$(uname -r)
cd linux-image-2.6 (I think this is the name of the directory)

Now save the following two patches as two separate files.

```

---

 Documentation/block/disk-protection.txt |   79 ++++++++++
 block/ll_rw_blk.c                       |  236 +++++++++++++++++++++++++++++++
 drivers/ata/libata-scsi.c               |   36 +++++
 drivers/ide/ide-disk.c                  |  142 +++++++++++++++++++
 drivers/ide/ide-io.c                    |   14 ++
 drivers/scsi/scsi_lib.c                 |  169 ++++++++++++++++++++++
 include/linux/ata.h                     |   12 ++
 include/linux/blkdev.h                  |   14 ++
 include/linux/ide.h                     |    1 
 9 files changed, 700 insertions(+), 3 deletions(-)

diff --git a/Documentation/block/disk-protection.txt b/Documentation/block/disk-protection.txt
new file mode 100644
index 0000000..508cc5b
--- /dev/null
+++ b/Documentation/block/disk-protection.txt
@@ -0,0 +1,79 @@
+Hard disk protection
+====================
+
+
+Intro
+-----
+ATA/ATAPI-7 specifies the IDLE IMMEDIATE command with UNLOAD FEATURE.
+Issuing this command should cause the drive to switch to idle mode and
+unload disk heads. This feature is being used in modern laptops in
+conjunction with accelerometers and appropriate software to implement
+a shock protection facility. The idea is to stop all I/O operations on
+the internal hard drive and park its heads on the ramp when critical
+situations are anticipated. The desire to have such a feature
+available on GNU/Linux systems has been the original motivation to
+implement a generic disk parking interface in the Linux kernel.
+
+
+The interface
+-------------
+The interface works as follows: Writing an integer value to
+/sys/block/*/queue/protect will park the respective drive and freeze
+the block layer queue for the specified number of seconds. When the
+timeout expires and no further disk park request has been issued in
+the meantime, the queue is unfrozen and accumulated I/O operations are
+performed.
+
+IMPORTANT NOTE:
+Not all ATA drives implement IDLE IMMEDIATE with UNLOAD FEATURE and
+quite a few of those that do so, don't report this capability as
+described in the specs. When a disk park has been requested through
+sysfs as described above, the kernel will try to determine if the
+drive supports the UNLOAD FEATURE by default. The kernel will only
+rely on the IDLE IMMEDIATE with UNLOAD FEATURE command if it is
+convinced that this command is actually supported by the disk drive;
+otherwise, it will fall back to STANDBY IMMEDIATE. Resuming from the
+latter will take much longer and it is generally more likely to have a
+negative impact on the drive's lifetime due to the inclease of spin
+down and up cycles. If you want to use this interface in a shock
+protection framework and you know that your drive does indeed support
+the IDLE IMMEDIATE with UNLOAD FEATURE command despite not saying so,
+you can force the kernel to issue that command by doing the following
+on the command line:
+# echo -n unload > /sys/block/sda/queue/protect_method
+(replace sda by the drive identifier as appropriate).
+
+/sys/block/*/queue/protect_method accepts auto, unload and standby
+respectively. Reading from protect_method shows the available options
+surrounding the active one with brackets. When auto is active, this
+will change to whatever the kernel sees fit after the next disk park
+command has been issued.
+
+
+References
+----------
+
+There are several laptops from different brands featuring shock
+protection capabilities. As manufacturers have refused to support open
+source development of the required software components so far, Linux
+support for shock protection varies considerably between different
+hardware implementations. Ideally, this section should contain a list
+of poiters at different projects aiming at an implementation of shock
+protection on different systeems. Unfortunately, I only know of a
+single project which, although still considered experimental, is fit
+for use. Please feel free to add projects that have been the victims
+of my ignorance.
+
+- http://www.thinkwiki.org/wiki/HDAPS
+  See this page for information about Linux support of the hard disk
+  active protection syystem as implemented in IBM/Lenovo Thinkpads.
+
+
+CREDITS
+-------
+
+The patch to implement the interface described in this file has
+originally been published by Jon Escombe <lists@...>.
+
+
+05 Dec 2006, Elias Oltmanns <eo@...>
diff --git a/block/ll_rw_blk.c b/block/ll_rw_blk.c
index 3b927be..356cfe3 100644
--- a/block/ll_rw_blk.c
+++ b/block/ll_rw_blk.c
@@ -39,6 +39,10 @@ #include <scsi/scsi_cmnd.h>

 static void blk_unplug_work(struct work_struct *work);
 static void blk_unplug_timeout(unsigned long data);
+static void blk_unfreeze_work(struct work_struct *work);
+static void blk_unfreeze_timeout(unsigned long data);
+static int blk_protect_register(struct request_queue *q);
+static void blk_protect_unregister(struct request_queue *q);
 static void drive_stat_acct(struct request *rq, int new_io);
 static void init_request_from_bio(struct request *req, struct bio *bio);
 static int __make_request(struct request_queue *q, struct bio *bio);
@@ -231,6 +235,16 @@ void blk_queue_make_request(struct reque
 	q->unplug_timer.function = blk_unplug_timeout;
 	q->unplug_timer.data = (unsigned long)q;

+	q->max_unfreeze = 30;
+
+	INIT_WORK(&q->unfreeze_work, blk_unfreeze_work);
+
+	q->unfreeze_timer.function = blk_unfreeze_timeout;
+	q->unfreeze_timer.data = (unsigned long)q;
+
+	/* Set protect_method to auto detection initially */
+	q->protect_method = 2;
+
 	/*
 	 * by default assume old behaviour and bounce for any highmem page
 	 */
@@ -263,6 +277,18 @@ static void rq_init(struct request_queue
 	rq->next_rq = NULL;
 }

+void blk_queue_issue_protect_fn(struct request_queue *q, issue_protect_fn *ipf)
+{
+	q->issue_protect_fn = ipf;
+}
+EXPORT_SYMBOL(blk_queue_issue_protect_fn);
+
+void blk_queue_issue_unprotect_fn(struct request_queue *q, issue_unprotect_fn *iuf)
+{
+	q->issue_unprotect_fn = iuf;
+}
+EXPORT_SYMBOL(blk_queue_issue_unprotect_fn);
+
 /**
  * blk_queue_ordered - does this queue support ordered writes
  * @q:        the request queue
@@ -1861,6 +1887,7 @@ struct request_queue *blk_alloc_queue_no
 	}

 	init_timer(&q->unplug_timer);
+	init_timer(&q->unfreeze_timer);

 	kobject_set_name(&q->kobj, "%s", "queue");
 	q->kobj.ktype = &queue_ktype;
@@ -4214,13 +4241,21 @@ int blk_register_queue(struct gendisk *d
 	kobject_uevent(&q->kobj, KOBJ_ADD);

 	ret = elv_register_queue(q);
+	if (ret)
+		goto err;
+
+	ret = blk_protect_register(q);
 	if (ret) {
-		kobject_uevent(&q->kobj, KOBJ_REMOVE);
-		kobject_del(&q->kobj);
-		return ret;
+		elv_unregister_queue(q);
+		goto err;
 	}

 	return 0;
+
+err:
+	kobject_uevent(&q->kobj, KOBJ_REMOVE);
+	kobject_del(&q->kobj);
+	return ret;
 }

 void blk_unregister_queue(struct gendisk *disk)
@@ -4228,6 +4263,7 @@ void blk_unregister_queue(struct gendisk
 	struct request_queue *q = disk->queue;

 	if (q && q->request_fn) {
+		blk_protect_unregister(q);
 		elv_unregister_queue(q);

 		kobject_uevent(&q->kobj, KOBJ_REMOVE);
@@ -4235,3 +4271,197 @@ void blk_unregister_queue(struct gendisk
 		kobject_put(&disk->kobj);
 	}
 }
+
+/*
+ * Issue lower level unprotect function if no timers are pending.
+ */
+static void blk_unfreeze_work(struct work_struct *work)
+{
+	struct request_queue *q = container_of(work, struct request_queue, unfreeze_work);
+	int pending;
+	unsigned long flags;
+
+	spin_lock_irqsave(q->queue_lock, flags);
+	pending = timer_pending(&q->unfreeze_timer);
+	spin_unlock_irqrestore(q->queue_lock, flags);
+	if (!pending)
+		q->issue_unprotect_fn(q);
+}
+
+/*
+ * Called when the queue freeze timeout expires...
+ */
+static void blk_unfreeze_timeout(unsigned long data)
+{
+	struct request_queue *q = (struct request_queue *) data;
+
+	kblockd_schedule_work(&q->unfreeze_work);
+}
+
+/*
+ * The lower level driver parks and freezes the queue, and this block layer
+ *  function sets up the freeze timeout timer on return. If the queue is
+ *  already frozen then this is called to extend the timer...
+ */
+void blk_freeze_queue(struct request_queue *q, int seconds)
+{
+	/* Don't accept arbitrarily long freezes */
+	if (seconds >= q->max_unfreeze)
+		seconds = q->max_unfreeze;
+	/* set/reset the timer */
+	mod_timer(&q->unfreeze_timer, msecs_to_jiffies(seconds*1000) + jiffies);
+}
+
+/*
+ * When reading the 'protect' attribute, we return seconds remaining
+ * before unfreeze timeout expires
+ */
+static ssize_t queue_protect_show(struct request_queue *q, char *page)
+{
+	unsigned int seconds = 0;
+
+	spin_lock_irq(q->queue_lock);
+	if (blk_queue_stopped(q) && timer_pending(&q->unfreeze_timer))
+		/*
+		 * Adding 1 in order to guarantee nonzero value until timer
+		 * has actually expired.
+		 */
+		seconds = jiffies_to_msecs(q->unfreeze_timer.expires
+					   - jiffies) / 1000 + 1;
+	spin_unlock_irq(q->queue_lock);
+	return queue_var_show(seconds, (page));
+}
+
+/*
+ * When writing the 'protect' attribute, input is the number of seconds
+ * to freeze the queue for. We call a lower level helper function to
+ * park the heads and freeze/block the queue, then we make a block layer
+ * call to setup the thaw timeout. If input is 0, then we thaw the queue.
+ */
+static ssize_t queue_protect_store(struct request_queue *q,
+				   const char *page, size_t count)
+{
+	unsigned long freeze = 0;
+
+	queue_var_store(&freeze, page, count);
+
+	if (freeze>0) {
+		/* Park and freeze */
+		if (!blk_queue_stopped(q))
+			q->issue_protect_fn(q);
+		/* set / reset the thaw timer */
+		spin_lock_irq(q->queue_lock);
+		blk_freeze_queue(q, freeze);
+		spin_unlock_irq(q->queue_lock);
+	} else {
+		spin_lock_irq(q->queue_lock);
+		freeze = del_timer(&q->unfreeze_timer);
+		spin_unlock_irq(q->queue_lock);
+		if (freeze)
+			q->issue_unprotect_fn(q);
+	}
+
+	return count;
+}
+
+static ssize_t
+queue_str_show(char *page, char *str, int status)
+{
+	ssize_t len;
+
+	if (status & 1)
+		len = sprintf(page, "[%s]", str);
+	else
+		len = sprintf(page, "%s", str);
+	if (status & 2)
+		len += sprintf(page+len, "\n");
+	else
+		len += sprintf(page+len, " ");
+	return len;
+}
+
+/*
+ * Returns current protect_method.
+ */
+static ssize_t queue_protect_method_show(struct request_queue *q, char *page)
+{
+	int len = 0;
+	int unload = q->protect_method;
+
+	len += queue_str_show(page+len, "auto", (unload & 2) >> 1);
+	len += queue_str_show(page+len, "unload", unload & 1);
+	len += queue_str_show(page+len, "standby", !unload ? 3 : 2);
+	return len;
+}
+
+/*
+ * Stores the device protect method.
+ */
+static ssize_t queue_protect_method_store(struct request_queue *q,
+				   const char *page, size_t count)
+{
+	spin_lock_irq(q->queue_lock);
+	if (!strcmp(page, "auto") || !strcmp(page, "auto\n"))
+		q->protect_method = 2;
+	else if (!strcmp(page, "unload") || !strcmp(page, "unload\n"))
+		q->protect_method = 1;
+	else if (!strcmp(page, "standby") || !strcmp(page, "standby\n"))
+		q->protect_method = 0;
+	else {
+		spin_unlock_irq(q->queue_lock);
+		return -EINVAL;
+	}
+	spin_unlock_irq(q->queue_lock);
+	return count;
+}
+
+static struct queue_sysfs_entry queue_protect_entry = {
+	.attr = { .name = "protect", .mode = S_IRUGO | S_IWUSR },
+	.show = queue_protect_show,
+	.store = queue_protect_store,
+};
+static struct queue_sysfs_entry queue_protect_method_entry = {
+	.attr = { .name = "protect_method", .mode = S_IRUGO | S_IWUSR },
+	.show = queue_protect_method_show,
+	.store = queue_protect_method_store,
+};
+
+static int blk_protect_register(struct request_queue *q)
+{
+	int error = 0;
+
+	/* check that the lower level driver has a protect handler */
+	if (!q->issue_protect_fn)
+		return 0;
+
+	/* create the attributes */
+	error = sysfs_create_file(&q->kobj, &queue_protect_entry.attr);
+	if (error) {
+		printk(KERN_ERR
+		       "blk_protect_register(): failed to create protect queue attribute!\n");
+		return error;
+	}
+
+	error = sysfs_create_file(&q->kobj, &queue_protect_method_entry.attr);
+	if (error) {
+		sysfs_remove_file(&q->kobj, &queue_protect_entry.attr);
+		printk(KERN_ERR
+		       "blk_protect_register(): failed to create protect_method attribute!\n");
+		return error;
+	}
+	kobject_get(&q->kobj);
+
+	return 0;
+}
+
+static void blk_protect_unregister(struct request_queue *q)
+{
+	/* check that the lower level driver has a protect handler */
+	if (!q->issue_protect_fn)
+		return;
+
+	/* remove the attributes */
+	sysfs_remove_file(&q->kobj, &queue_protect_method_entry.attr);
+	sysfs_remove_file(&q->kobj, &queue_protect_entry.attr);
+	kobject_put(&q->kobj);
+}
diff --git a/drivers/ata/libata-scsi.c b/drivers/ata/libata-scsi.c
index 94144ed..393f1d5 100644
--- a/drivers/ata/libata-scsi.c
+++ b/drivers/ata/libata-scsi.c
@@ -853,6 +853,38 @@ static void ata_scsi_dev_config(struct s
 	}
 }

+extern int scsi_protect_queue(struct request_queue *q, int unload);
+extern int scsi_unprotect_queue(struct request_queue *q);
+
+static int ata_scsi_issue_protect_fn(struct request_queue *q)
+{
+	struct scsi_device *sdev = q->queuedata;
+	struct ata_port *ap = ata_shost_to_port(sdev->host);
+	struct ata_device *dev = ata_scsi_find_dev(ap, sdev);
+	int unload = q->protect_method;
+	unsigned long flags;
+
+	if (!dev) {
+		printk(KERN_DEBUG "ata_scsi_issue_protect_fn(): Couldn't find ATA device to be parked.\n");
+		return -ENXIO;
+	}
+
+	if (unload == 2) {
+		unload = ata_id_has_unload(dev->id) ? 1 : 0;
+		spin_lock_irqsave(q->queue_lock, flags);
+		q->protect_method = unload;
+		spin_unlock_irqrestore(q->queue_lock, flags);
+	}
+
+	/* call scsi_protect_queue, requesting either unload or standby */
+	return scsi_protect_queue(q, unload);
+}
+
+static int ata_scsi_issue_unprotect_fn(struct request_queue *q)
+{
+	return scsi_unprotect_queue(q);
+}
+
 /**
  *	ata_scsi_slave_config - Set SCSI device attributes
  *	@sdev: SCSI device to examine
@@ -876,6 +908,10 @@ int ata_scsi_slave_config(struct scsi_de

 	if (dev)
 		ata_scsi_dev_config(sdev, dev);
+	blk_queue_issue_protect_fn(sdev->request_queue,
+		ata_scsi_issue_protect_fn);
+	blk_queue_issue_unprotect_fn(sdev->request_queue,
+		ata_scsi_issue_unprotect_fn);

 	return 0;	/* scsi layer doesn't check return value, sigh */
 }
diff --git a/drivers/ide/ide-disk.c b/drivers/ide/ide-disk.c
index 00123d9..a54e2f2 100644
--- a/drivers/ide/ide-disk.c
+++ b/drivers/ide/ide-disk.c
@@ -701,6 +701,145 @@ static void idedisk_prepare_flush(struct
 }

 /*
+ * todo:
+ *  - we freeze the queue regardless of success and rely on the
+ *    ide_protect_queue function to thaw immediately if the command
+ *    failed (to be consistent with the libata handler)... should
+ *    we also inspect here?
+ */
+void ide_end_protect_rq(struct request *rq, int error)
+{
+	struct completion *waiting = rq->end_io_data;
+
+	rq->end_io_data = NULL;
+	/* spin lock already accquired */
+	if (!blk_queue_stopped(rq->q))
+		blk_stop_queue(rq->q);
+
+	complete(waiting);
+}
+
+int ide_unprotect_queue(struct request_queue *q)
+{
+	struct request rq;
+	unsigned long flags;
+	int pending = 0, rc = 0;
+	ide_drive_t *drive = q->queuedata;
+	u8 args[7], *argbuf = args;
+
+	if (!blk_queue_stopped(q))
+		return -EIO;
+
+	/* Are there any pending jobs on the queue? */
+	pending = ((q->rq.count[READ] > 0) || (q->rq.count[WRITE] > 0)) ? 1 : 0;
+
+	spin_lock_irqsave(q->queue_lock, flags);
+	blk_start_queue(q);
+	spin_unlock_irqrestore(q->queue_lock, flags);
+
+	/* The unload feature of the IDLE_IMMEDIATE command
+	   temporarily disables HD power management from spinning down
+	   the disk. Any other command will reenable HD pm, so, if
+	   there are no pending jobs on the queue, another
+	   CHECK_POWER_MODE1 command without the unload feature should do
+	   just fine. */
+	if (!pending) {
+		printk(KERN_DEBUG "ide_unprotect_queue(): No pending I/O, re-enabling power management..\n");
+		memset(args, 0, sizeof(args));
+		argbuf[0] = 0xe5; /* CHECK_POWER_MODE1 */
+		ide_init_drive_cmd(&rq);
+		rq.cmd_type = REQ_TYPE_ATA_TASK;
+		rq.buffer = argbuf;
+		rc = ide_do_drive_cmd(drive, &rq, ide_head_wait);
+	}
+
+	return rc;
+}
+
+int ide_protect_queue(struct request_queue *q, int unload)
+{
+	ide_drive_t *drive = q->queuedata;
+	struct request rq;
+	u8 args[7], *argbuf = args;
+	int ret = 0;
+	DECLARE_COMPLETION(wait);
+
+	memset(&rq, 0, sizeof(rq));
+	memset(args, 0, sizeof(args));
+
+	if (blk_queue_stopped(q))
+		return -EIO;
+
+	if (unload) {
+		argbuf[0] = 0xe1;
+		argbuf[1] = 0x44;
+		argbuf[3] = 0x4c;
+		argbuf[4] = 0x4e;
+		argbuf[5] = 0x55;
+	} else
+		argbuf[0] = 0xe0;
+
+	/* Issue the park command & freeze */
+	ide_init_drive_cmd(&rq);
+
+	rq.cmd_type = REQ_TYPE_ATA_TASK;
+	rq.buffer = argbuf;
+	rq.end_io_data = &wait;
+	rq.end_io = ide_end_protect_rq;
+
+	ret = ide_do_drive_cmd(drive, &rq, ide_next);
+	wait_for_completion(&wait);
+
+	if (ret)
+	{
+		printk(KERN_DEBUG "ide_protect_queue(): Warning: head NOT parked!..\n");
+		ide_unprotect_queue(q);
+		return ret;
+	}
+
+	if (unload) {
+		if (args[3] == 0xc4)
+			printk(KERN_DEBUG "ide_protect_queue(): head parked..\n");
+		else {
+			/* error parking the head */
+			printk(KERN_DEBUG "ide_protect_queue(): head NOT parked!..\n");
+			ret = -EIO;
+			ide_unprotect_queue(q);
+		}
+	} else
+		printk(KERN_DEBUG "ide_protect_queue(): head park not requested, used standby!..\n");
+
+	return ret;
+}
+
+int idedisk_issue_protect_fn(struct request_queue *q)
+{
+	ide_drive_t *drive = q->queuedata;
+	int unload = q->protect_method;
+	unsigned long flags;
+
+	/*
+	 * Check capability of the device -
+	 *  - if "idle immediate with unload" is supported we use that, else
+	 *    we use "standby immediate" and live with spinning down the drive..
+	 *    (Word 84, bit 13 of IDENTIFY DEVICE data)
+	 */
+	if (unload == 2) {
+		unload = drive->id->cfsse & (1 << 13) ? 1 : 0;
+		spin_lock_irqsave(q->queue_lock, flags);
+		q->protect_method = unload;
+		spin_unlock_irqrestore(q->queue_lock, flags);
+	}
+
+	return ide_protect_queue(q, unload);
+}
+
+int idedisk_issue_unprotect_fn(struct request_queue *q)
+{
+	return ide_unprotect_queue(q);
+}
+
+/*
  * This is tightly woven into the driver->do_special can not touch.
  * DON'T do it again until a total personality rewrite is committed.
  */
@@ -972,6 +1111,9 @@ static void idedisk_setup (ide_drive_t *
 		drive->wcache = 1;

 	write_cache(drive, 1);
+
+	blk_queue_issue_protect_fn(drive->queue, idedisk_issue_protect_fn);
+	blk_queue_issue_unprotect_fn(drive->queue, idedisk_issue_unprotect_fn);
 }

 static void ide_cacheflush_p(ide_drive_t *drive)
diff --git a/drivers/ide/ide-io.c b/drivers/ide/ide-io.c
index db22d1f..1e54733 100644
--- a/drivers/ide/ide-io.c
+++ b/drivers/ide/ide-io.c
@@ -1270,6 +1270,17 @@ #endif
 		}

 		/*
+		 * Don't accept a request when the queue is stopped (unless we
+		 * are resuming from suspend). Prevents existing queue entries
+		 * being processed after queue is stopped by the hard disk
+		 * protection mechanism...
+		 */
+		if (test_bit(QUEUE_FLAG_STOPPED, &drive->queue->queue_flags) && !blk_pm_resume_request(rq)) {
+			hwgroup->busy = 0;
+			break;
+		}
+
+		/*
 		 * Sanity: don't accept a request that isn't a PM request
 		 * if we are currently power managed. This is very important as
 		 * blk_stop_queue() doesn't prevent the elv_next_request()
@@ -1767,6 +1778,9 @@ int ide_do_drive_cmd (ide_drive_t *drive
 		where = ELEVATOR_INSERT_FRONT;
 		rq->cmd_flags |= REQ_PREEMPT;
 	}
+	if (action == ide_next)
+		where = ELEVATOR_INSERT_FRONT;
+
 	__elv_add_request(drive->queue, rq, where, 0);
 	ide_do_request(hwgroup, IDE_NO_IRQ);
 	spin_unlock_irqrestore(&ide_lock, flags);
diff --git a/drivers/scsi/scsi_lib.c b/drivers/scsi/scsi_lib.c
index 0e81e4c..895b1f4 100644
--- a/drivers/scsi/scsi_lib.c
+++ b/drivers/scsi/scsi_lib.c
@@ -2268,7 +2268,13 @@ EXPORT_SYMBOL_GPL(sdev_evt_send_simple);
 int
 scsi_device_quiesce(struct scsi_device *sdev)
 {
+	int i;
 	int err = scsi_device_set_state(sdev, SDEV_QUIESCE);
+	for (i = 0; err && (sdev->sdev_state == SDEV_BLOCK) && (i < 100);
+	     i++) {
+		msleep_interruptible(200);
+		err = scsi_device_set_state(sdev, SDEV_QUIESCE);
+	}
 	if (err)
 		return err;

@@ -2518,3 +2524,166 @@ void scsi_kunmap_atomic_sg(void *virt)
 	kunmap_atomic(virt, KM_BIO_SRC_IRQ);
 }
 EXPORT_SYMBOL(scsi_kunmap_atomic_sg);
+
+/*
+ * Structure required for synchronous io completion after queue freezing
+ */
+struct scsi_protect_io_context_sync {
+	struct scsi_device *sdev;
+	int result;
+	char *sense;
+	struct completion *waiting;
+};
+
+/*
+ * scsi_protect_wait_done()
+ * Command completion handler for scsi_protect_queue().
+ *
+ * Unable to call scsi_internal_device_block() as
+ * scsi_end_request() already has the spinlock. So,
+ * we put the necessary functionality inline.
+ *
+ * todo:
+ *  - we block the queue regardless of success and rely on the
+ *    scsi_protect_queue function to unblock if the command
+ *    failed... should we also inspect here?
+ */
+static void scsi_protect_wait_done(void *data, char *sense, int result, int resid)
+{
+	struct scsi_protect_io_context_sync *siocs = data;
+	struct completion *waiting = siocs->waiting;
+	struct request_queue *q = siocs->sdev->request_queue;
+
+	siocs->waiting = NULL;
+	siocs->result = result;
+	memcpy(siocs->sense, sense, SCSI_SENSE_BUFFERSIZE);
+
+	if (!scsi_device_set_state(siocs->sdev, SDEV_BLOCK))
+		blk_stop_queue(q);
+
+	complete(waiting);
+}
+
+/*
+ * scsi_unprotect_queue()
+ *  - release the queue that was previously blocked
+ */
+int scsi_unprotect_queue(struct request_queue *q)
+{
+	struct scsi_device *sdev = q->queuedata;
+	int rc = 0, pending = 0;
+	u8 scsi_cmd[MAX_COMMAND_SIZE];
+	struct scsi_sense_hdr sshdr;
+
+	if (sdev->sdev_state != SDEV_BLOCK)
+		return -ENXIO;
+
+	/* Are there any pending jobs on the queue? */
+	pending = ((q->rq.count[READ] > 0) || (q->rq.count[WRITE] > 0)) ? 1 : 0;
+
+	rc = scsi_internal_device_unblock(sdev);
+	if (rc)
+		return rc;
+
+	if (!pending) {
+		printk(KERN_DEBUG "scsi_unprotect_queue(): No pending I/O, re-enabling power management..\n");
+
+		memset(scsi_cmd, 0, sizeof(scsi_cmd));
+		scsi_cmd[0]  = ATA_16;
+		scsi_cmd[1]  = (3 << 1); /* Non-data */
+		/* scsi_cmd[2] is already 0 -- no off.line, cc, or data xfer */
+		scsi_cmd[14] = 0xe5; /* CHECK_POWER_MODE1 */
+
+		/* Good values for timeout and retries?  Values below
+   		   from scsi_ioctl_send_command() for default case... */
+		if (scsi_execute_req(sdev, scsi_cmd, DMA_NONE, NULL, 0, &sshdr,
+		   		     (10*HZ), 5))
+			rc = -EIO;
+	}
+	return rc;
+}
+EXPORT_SYMBOL_GPL(scsi_unprotect_queue);
+
+/*
+ * scsi_protect_queue()
+ *  - build and issue the park/standby command..
+ *  - queue is blocked during command completion handler
+ */
+int scsi_protect_queue(struct request_queue *q, int unload)
+{
+	struct scsi_protect_io_context_sync siocs;
+	struct scsi_device *sdev = q->queuedata;
+	int rc = 0;
+	u8 args[7];
+	u8 scsi_cmd[MAX_COMMAND_SIZE];
+	unsigned char sense[SCSI_SENSE_BUFFERSIZE];
+	unsigned char *desc;
+	DECLARE_COMPLETION_ONSTACK(wait);
+
+	if (sdev->sdev_state != SDEV_RUNNING)
+		return -ENXIO;
+
+	memset(args, 0, sizeof(args));
+	memset(sense, 0, sizeof(sense));
+
+	if (unload) {
+		args[0] = 0xe1;
+		args[1] = 0x44;
+		args[3] = 0x4c;
+		args[4] = 0x4e;
+		args[5] = 0x55;
+	} else
+		args[0] = 0xe0;
+
+	memset(scsi_cmd, 0, sizeof(scsi_cmd));
+	scsi_cmd[0]  = ATA_16;
+	scsi_cmd[1]  = (3 << 1); /* Non-data */
+	scsi_cmd[2]  = 0x20;     /* no off.line, or data xfer, request cc */
+	scsi_cmd[4]  = args[1];
+	scsi_cmd[6]  = args[2];
+	scsi_cmd[8]  = args[3];
+	scsi_cmd[10] = args[4];
+	scsi_cmd[12] = args[5];
+	scsi_cmd[14] = args[0];
+	siocs.sdev = sdev;
+	siocs.sense = sense;
+	siocs.waiting = &wait;
+
+	scsi_execute_async(sdev, scsi_cmd, COMMAND_SIZE(scsi_cmd[0]),
+			   DMA_NONE, NULL, 0, 0, (10*HZ), 5,
+			   &siocs, &scsi_protect_wait_done, GFP_NOWAIT);
+	wait_for_completion(&wait);
+
+	if (siocs.result != ((DRIVER_SENSE << 24) + SAM_STAT_CHECK_CONDITION)) {
+		printk(KERN_DEBUG "scsi_protect_queue(): head NOT parked!..\n");
+		scsi_unprotect_queue(q);		/* just in case we still managed to block */
+		rc = -EIO;
+		goto out;
+	}
+
+	desc = sense + 8;
+
+	/* Retrieve data from check condition */
+	args[1] = desc[3];
+	args[2] = desc[5];
+	args[3] = desc[7];
+	args[4] = desc[9];
+	args[5] = desc[11];
+	args[0] = desc[13];
+
+	if (unload) {
+		if (args[3] == 0xc4)
+			printk(KERN_DEBUG "scsi_protect_queue(): head parked..\n");
+		else {
+			/* error parking the head */
+			printk(KERN_DEBUG "scsi_protect_queue(): head NOT parked!..\n");
+			rc = -EIO;
+			scsi_unprotect_queue(q);
+		}
+	} else
+		printk(KERN_DEBUG "scsi_protect_queue(): head park not requested, used standby!..\n");
+
+out:
+	return rc;
+}
+EXPORT_SYMBOL_GPL(scsi_protect_queue);
diff --git a/include/linux/ata.h b/include/linux/ata.h
index 5c4e54a..d501029 100644
--- a/include/linux/ata.h
+++ b/include/linux/ata.h
@@ -380,6 +380,18 @@ #define ata_id_u64(id,n)	\

 #define ata_id_cdb_intr(id)	(((id)[0] & 0x60) == 0x20)

+static inline int ata_id_has_unload(const u16 *id)
+{
+	/* ATA-7 specifies two places to indicate unload feature support.
+	 * Since I don't really understand the difference, I'll just check
+	 * both and only return zero if none of them indicates otherwise. */
+	if ((id[84] & 0xC000) == 0x4000 && id[84] & (1 << 13))
+		return id[84] & (1 << 13);
+	if ((id[87] & 0xC000) == 0x4000)
+		return id[87] & (1 << 13);
+	return 0;
+}
+
 static inline bool ata_id_has_hipm(const u16 *id)
 {
 	u16 val = id[76];
diff --git a/include/linux/blkdev.h b/include/linux/blkdev.h
index d18ee67..e10f40b 100644
--- a/include/linux/blkdev.h
+++ b/include/linux/blkdev.h
@@ -332,6 +332,8 @@ struct bio_vec;
 typedef int (merge_bvec_fn) (struct request_queue *, struct bio *, struct bio_vec *);
 typedef void (prepare_flush_fn) (struct request_queue *, struct request *);
 typedef void (softirq_done_fn)(struct request *);
+typedef int (issue_protect_fn) (struct request_queue *);
+typedef int (issue_unprotect_fn) (struct request_queue *);

 enum blk_queue_state {
 	Queue_down,
@@ -368,6 +370,8 @@ struct request_queue
 	merge_bvec_fn		*merge_bvec_fn;
 	prepare_flush_fn	*prepare_flush_fn;
 	softirq_done_fn		*softirq_done_fn;
+	issue_protect_fn	*issue_protect_fn;
+	issue_unprotect_fn	*issue_unprotect_fn;

 	/*
 	 * Dispatch queue sorting
@@ -383,6 +387,14 @@ struct request_queue
 	unsigned long		unplug_delay;	/* After this many jiffies */
 	struct work_struct	unplug_work;

+	/*
+	 * Auto-unfreeze state
+	 */
+	struct timer_list	unfreeze_timer;
+	int			max_unfreeze;	/* At most this many seconds */
+	struct work_struct	unfreeze_work;
+	int			protect_method;
+
 	struct backing_dev_info	backing_dev_info;

 	/*
@@ -773,6 +785,8 @@ extern int blk_do_ordered(struct request
 extern unsigned blk_ordered_cur_seq(struct request_queue *);
 extern unsigned blk_ordered_req_seq(struct request *);
 extern void blk_ordered_complete_seq(struct request_queue *, unsigned, int);
+extern void blk_queue_issue_protect_fn(struct request_queue *, issue_protect_fn *);
+extern void blk_queue_issue_unprotect_fn(struct request_queue *, issue_unprotect_fn *);

 extern int blk_rq_map_sg(struct request_queue *, struct request *, struct scatterlist *);
 extern void blk_dump_rq_flags(struct request *, char *);
diff --git a/include/linux/ide.h b/include/linux/ide.h
index dc75ccb..990cac2 100644
--- a/include/linux/ide.h
+++ b/include/linux/ide.h
@@ -1045,6 +1045,7 @@ extern void ide_init_drive_cmd (struct r
  */
 typedef enum {
 	ide_wait,	/* insert rq at end of list, and wait for it */
+	ide_next,	/* insert rq immediately after current request */
 	ide_preempt,	/* insert rq in front of current request */
 	ide_head_wait,	/* insert rq in front of current request and wait for it */
 	ide_end		/* insert rq at end of list, but don't wait for it */

```

```
---

 drivers/ata/libata-scsi.c |    4 ++--
 1 files changed, 2 insertions(+), 2 deletions(-)

diff --git a/drivers/ata/libata-scsi.c b/drivers/ata/libata-scsi.c
index 14daf48..bab372b 100644
--- a/drivers/ata/libata-scsi.c
+++ b/drivers/ata/libata-scsi.c
@@ -823,7 +823,7 @@ static void ata_scsi_sdev_config(struct 
 	 * prevent SCSI midlayer from automatically deferring
 	 * requests.
 	 */
-	sdev->max_device_blocked = 1;
+	sdev->max_device_blocked = 2;
 }
 
 static void ata_scsi_dev_config(struct scsi_device *sdev,
@@ -3120,7 +3120,7 @@ int ata_scsi_add_hosts(struct ata_host *
 		 * Set host_blocked to 1 to prevent SCSI midlayer from
 		 * automatically deferring requests.
 		 */
-		shost->max_host_blocked = 1;
+		shost->max_host_blocked = 2;
 
 		rc = scsi_add_host(ap->scsi_host, ap->host->dev);
 		if (rc)

```

Now, from the directory of the kernel source:

patch -p1 -i <name of patch1>
patch -p1 -i <name of patch2>

Now, "make oldconfig".  This should not ask you any questions.

Finally:

make-kpkg --initrd --rootcmd fakeroot kernel_image
sudo dpkg i ../linux*.deb

---

### Post by sotirisp on 2008-08-09
First of all,

Infinity thank you for your help, your effort to guide me and the time you spent writing the commands to be carried out.

After following your instructions:

Doesn't work. Apart from the HDAPS that shows always a status of Running hard disk (even if i drop my laptop down from the sky), i run into more problems after patching and installing the kernel.

I now have WIFI AND Sound not working.

Thanks again anyway, seems that linux in general has a long way yet to be able to support technologies that are even 3 years old (IBM's APS).

I'll stick to my Windows XP for the laptop...

STATUS: Thinkpad T43 - Ubuntu Hardy - Patched kernel for HDAPS -> Not working.

---

### Post by InfinityCircuit on 2008-08-09
I'm sorry you couldn't get it to work for you.  I experienced a similar problem with loss of sound and don't use APS myself for that reason.  All in all, HDAPS has never saved my data and has only drained my battery life.  By the way, the fix for your wifi is easy: just sudo cp -a /lib/firmware/2.6.24-generic-19/* /lib/firmware/ and reboot.

---

