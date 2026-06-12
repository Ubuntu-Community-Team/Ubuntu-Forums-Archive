---
title: "Can someone please help me!!!!!"
date: 2005-12-01
forum: Programming Talk
---

### Post by ScottLH on 2005-12-01
I am try to in stall a driver from cd rom using the terminal. I know how to get root, But I can't seem to get the file to run.It keeps teeling me that file is not directory or something to that effect.
I've tried,
ls /media/cdrom

cd /media/cdrom

sh NVIDIA-Linux-x86_64-1.0-0130-pkg1.run
Then it tells me that it is not directory or no such file.
Does anyone know how to do this? I remeber commands along this line helped before
CD /
ls
cdrom
but I think I am doing it wrong because now I cannot do it, I got it to run before, but I needed root. Know I found out how to do root, but I cannot remember how input the commands correctly.
Please Help.
  	
Reply With Quote

---

### Post by cactus on 2005-12-01
mount /media/cdrom
cd ~
mkdir working
cd /media/cdrom
ls
# assumes filename is NVIDIA-blah blah blah
cp NVIDIA* ~/working
cd ~/working
chmod 755 NVIDIA*
sh NVIDIA*

??

---

### Post by ScottLH on 2005-12-01
I tried what you suggested and it said the cdrom was already mounted. It did not work. Maybe I entered it wrong. Can you show me how it would look if you did it in the terminal.

---

### Post by cactus on 2005-12-01
well, if it automounted it, then you can safely skip that step. The rest should be applicable.

I am away from my box right now..so I am not able to replicate the output verbatim.

---

