---
title: "Fat32 system serious problems"
date: 2012-07-01
forum: New to Ubuntu
---

### Post by mnimonios on 2012-07-01
Hi guys, happy to be part of the forum. Your lights please. I have a multi-boot system, with memory tested 100% OK and no other issues (except the common firefox crashes now and then)  and have partitioned (with provided tools)  a ~230 GB disk part as FAT32 for file storage and access from other OS'es. To avoid missleading you I must say that for a long time now I only boot Ubuntu 10.04 LTS, and the issue is that many  files on my FAT32 partition get randomly CORRUPTED. Their names appear OK on file manager but with size of 0 bytes, in other words their content get lost. And I have lost a big number of usefull files, some of them difficult to get again. The disk is in perfect condition, even tested with spinrite etc, so I tend to believe there is some serious OS issue working with big Fat32 partitions, and may I also say that this must be an old problem because I had seen similar problem with 8.04 LTS and didn't pay much attention. (Anyway, in smaller FAT32s like sticks and smaller disks never had a problem). Has anyone used big FAT32 partitions with ubuntu with similar problems?

---

### Post by westie457 on 2012-07-01
Welcome to the Forum.

Personally I only use NTFS and Ext4 partitions on hard drives only because there is no file size limit in normal usage. The FAT32 file-system can take a maximum file size of 4GB.

Are you dual-booting with Windows and hibernating/sleeping Windows?

Windows automatically mounts all available partitions (drives) and if Windows is not fully shutdown the partition is still mounted. When you then boot into Ubuntu and write to any of those partitions Windows will not recognize them in the Master File Table and wipe the data to do with those files.

If you are not hibernating Windows then I am not sure what could be causing the issue you have.

---

### Post by mnimonios on 2012-07-01
Hi, thanks for taking the time to reply. I haven't conciously used hibernating. Have pressed by mistake the keybord button that does it a couple of times, and recovering from hibbernation was not tottaly succesfull if I recall, (some add-on card issue?), so had to reboot. But my grub default OS is Ubuntu so don't think windows had any chance to do anything nasty (lol)

---

### Post by HermanAB on 2012-07-01
Yup, hibernate/suspend is the problem.  Don't do that if your dual boot.

Also, you should convert that FAT partition to something with a journal, such as NTFS.

---

### Post by mnimonios on 2012-07-01
You raised my suspicions on that. I think I'll open my keyboard and cripple the hibernate button. That's sadly the only way not to press it again by mistake, things can get very untidy here sometimes. But I'll try to resque useful staff first. Thanks guys.

---

