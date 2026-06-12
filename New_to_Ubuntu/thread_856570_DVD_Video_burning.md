---
title: "DVD Video burning"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by batty on 2008-07-11
Hello,
Since upgrading to K/Ubuntu 8.04 I am unable to burn Video Dvds.
I've tried K3b and Brasero both have same problem,always used to work before upgrade.
I seem able to burn to the DVD but it can't be played back in a DVD player or on PC.

Any ideas or is this a bug in Hardy?

Cheers Dave

---

### Post by TeoBigusGeekus on 2008-07-11
Have you tried burning data dvd's?
Do they work, i.e. are they recognised by the pc or not?

---

### Post by LowSky on 2008-07-11
Did you update you repos?

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

```
sudo apt-get install libdvdcss2
```

```
sudo apt-get install w32codecs
```

---

### Post by batty on 2008-07-11
Yeah data CDs and DVDs burn fine.
It's just video DVDs that seem to be the problem.

I will give Nero a go to see if that has any better luck, didn't really want to use Nero. Seems silly to pay for something I got free with my drive for windows.

Cheers Dave

---

### Post by TeoBigusGeekus on 2008-07-11
What do you mean when you say video dvd's? 
Are you trying to copy a dvd, rip a dvd or something else?

---

### Post by fiddledd on 2008-07-11
There's a thread here about problems with Kubuntu 8.04 and DVD burning. I haven't read it all, but it might be worth a read:

[http://ubuntuforums.org/showthread.php?t=787299](http://ubuntuforums.org/showthread.php?t=787299)

---

### Post by batty on 2008-07-13
Heres the Bradsero log I get when Video DVD burn fails.

BraseroGrowisofs called brasero_job_get_fd_in
BraseroGrowisofs called brasero_job_get_current_track
BraseroGrowisofs called brasero_job_get_input_type
BraseroGrowisofs called brasero_job_get_tmp_dir
BraseroGrowisofs called brasero_job_get_action
BraseroGrowisofs called brasero_job_set_current_action
BraseroGrowisofs got varg:
	growisofs
	-use-the-force-luke=notray
	-use-the-force-luke=dao
	-dvd-compat
	-speed=8
	-use-the-force-luke=tty
	-Z
	/dev/scd0
	-dry-run
	-r
	-J
	-dvd-video
	-input-charset
	utf8
	-graft-points
	-D
	-path-list
	/tmp/brasero_tmp_K574DU
	-exclude-list
	/tmp/brasero_tmp_EJ34DU
	-print-size
BraseroGrowisofs launching command
BraseroGrowisofs called brasero_job_get_fd_out
BraseroGrowisofs stdout: Executing 'genisoimage -r -J -dvd-video -input-charset utf8 -graft-points -D -path-list /tmp/brasero_tmp_K574DU -exclude-list /tmp/brasero_tmp_EJ34DU -print-size | builtin_dd of=/dev/scd0 obs=32k seek=0'
BraseroGrowisofs called brasero_job_set_dangerous
BraseroGrowisofs stderr: Warning: Disabling Joliet support for DVD-Video.
BraseroGrowisofs stderr: genisoimage: No such file or directory. Can't stat 
BraseroGrowisofs stderr: genisoimage: Can't open device ''
BraseroGrowisofs stderr: genisoimage: Unable to parse DVD-Video structures.
BraseroGrowisofs stderr: genisoimage: Could not find correct 'VIDEO_TS' directory.
BraseroGrowisofs stderr: genisoimage: Unable to make a DVD-Video image.
BraseroGrowisofs stdout: HUP
BraseroGrowisofs stderr: Possible reasons:
BraseroGrowisofs stderr:   - VIDEO_TS subdirectory was not found on specified location
BraseroGrowisofs stderr:   - VIDEO_TS has invalid contents
BraseroGrowisofs stderr: HUP
BraseroGrowisofs process finished with status 5
BraseroGrowisofs called brasero_job_error
BraseroGrowisofs finished with an error
BraseroGrowisofs asked to stop because of an error
	error		= 0
	message	= "no message"
BraseroGrowisofs stopping
BraseroGrowisofs got killed
Session error : unknown (brasero_burn_record burn.c:2273)

Despite what the log says all files are valid.

Dave

---

