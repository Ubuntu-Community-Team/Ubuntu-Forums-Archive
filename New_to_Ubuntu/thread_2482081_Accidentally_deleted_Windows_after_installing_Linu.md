---
title: "Accidentally deleted Windows after installing Linux"
date: 2022-12-19
forum: New to Ubuntu
---

### Post by fung0808 on 2022-12-19
After I installed Linux (Lubuntu), I realize that I might have accidentally deleted Windows, below I have attached a screenshot of the output when I enter

```
sudo fdisk -l
```



 in my terminal.


  I am thinking to delete /dev/nvme0n1p2 and /dev/nvme0n1p4 partitions and re-install Windows again for dual-booting.
 Is this the right direction? Thank you!!

---

### Post by speartip on 2022-12-19
If you wish to dual boot, you'll need to shrink your Linux partition (nvme0n1p3) by the size you wish your windows partition to be. Format the space you've created as NTFS, then install Windows on that.
Gparted should be able to help you with that.

---

### Post by QIII on 2022-12-19
I believe the user is saying that they had Windows installed, attempted to install Ubuntu (presumably as a dual boot) and wiped out Windows.

If such is the case, the user may not have installation media.

The question is:  How to restore the Windows installation.

---

### Post by speartip on 2022-12-19
So first question. Do you have your Windows installation media to boot from?

---

### Post by QIII on 2022-12-19
... and, do you have your backups handy?

---

### Post by VMC on 2022-12-19
You have recovery environment partition. Go here to read what WinRe is and what you can do with it:
[https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference?view=windows-11](https://learn.microsoft.com/en-us/windows-hardware/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference?view=windows-11)

---

### Post by ActionParsnip on 2022-12-20
Install Windows but leave space for Ubuntu unpartitioned and unallocated. You can then install Ubuntu to the space

---

### Post by mIk3_08 on 2022-12-20
> **fung0808 said:**
> After I installed Linux (Lubuntu), I realize that I might have accidentally deleted Windows, below I have attached a screenshot of the output when I enter

```
sudo fdisk -l
```



 in my terminal.


  I am thinking to delete /dev/nvme0n1p2 and /dev/nvme0n1p4 partitions and re-install Windows again for dual-booting.
 Is this the right direction? Thank you!!
Your /dev/nvme0n1p2 is only 16MB you can't use that one for your MS Windows. I prefer you create another unallocated partition for your MS Windows coming from your /dev/nvme0n1p3. Once done, then install MS Windows on it. You can't just install and uninstall on your drive. You just have to plan first before going into action. You can easily choose "along side with MS Windows" If you want dual boot in your system. You should have be careful in reading instructions so that you don't accidentally delete important files in your system. In this case, you should have to create another unallocated partition then be careful which partition you should choose when installing other Operating System.
Example: For placing the other operating system to other newly created partition. Once you knew that, you will never gonna erase your existing other Operating System. Regards and cheers

---

### Post by donald187 on 2022-12-21
> **QIII said:**
> I believe the user is saying that they had Windows installed, attempted to install Ubuntu (presumably as a dual boot) and wiped out Windows.

If such is the case, the user may not have installation media.

The question is:  How to restore the Windows installation.

 VMC's post on the recovery partition may be better but with Dell you can also download a recovery ISO image.[URL="https://www.dell.com/support/kbdoc/en-za/000132479/how-to-install-windows-10-from-a-dell-windows-10-recovery-dvd"]
[/URL]

---

### Post by QIII on 2022-12-21
Yes.  I understand that.

What is being described in that post is re-installation, not recovery/restoration.  While re-installation may be necessary, nobody has mentioned recovering the OP's files and data.

You will note that I asked about the OP's backups, which likely do not exist.  We do not have an answer to that yet.  Nobody has indicated to the OP whether or not they can recover their data in the machine's present state.  Nobody has said anything to indicate to the OP that re-installation will not restore data, but make it unrecoverable at this point.  

Any attempt at data recovery, if it will work, will need to happen before re-installing.

That being the case, any discussion of how to "recover" the Windows installation will necessarily start with a discussion of the feasibility of data recovery.

---

### Post by speartip on 2022-12-21
I would think that because the whole Windows partition has been reformatted to EXT4, then overwritten by Ubuntu, that data recovery would be nigh on impossible. Backups would be the only option if they exist. We would need to hear from the OP on that.

---

### Post by VMC on 2022-12-21
> **speartip said:**
> I would think that because the whole Windows partition has been reformatted to EXT4, then overwritten by Ubuntu, that data recovery would be nigh on impossible. Backups would be the only option if they exist. We would need to hear from the OP on that.
Yes, agreed, plus that fact, the OP has not returned. All our suggestions have gone unanswered.

---

### Post by donald187 on 2022-12-21
> **QIII said:**
> Yes.  I understand that.

Sorry.  I didn't mean to tell *you* that.  I should have indicated that I was speaking to the OP.

> 
What is being described in that post is re-installation, not recovery/restoration.  While re-installation may be necessary, nobody has mentioned recovering the OP's files and data.

You will note that I asked about the OP's backups, which likely do not exist.  We do not have an answer to that yet.  Nobody has indicated to the OP whether or not they can recover their data in the machine's present state.  Nobody has said anything to indicate to the OP that re-installation will not restore data, but make it unrecoverable at this point.  

Any attempt at data recovery, if it will work, will need to happen before re-installing.

That being the case, any discussion of how to "recover" the Windows installation will necessarily start with a discussion of the feasibility of data recovery.
Got it.

---

### Post by mIk3_08 on 2022-12-22
> **QIII said:**
> Yes.  I understand that.
What is being described in that post is re-installation, not recovery/restoration.
I agree with QIII's  recovery is not possible solution to this mess. If the OP are to do recovery this might damage the existing newly installed Linux Ubuntu Operating System. For me, just continue the mess but if the OP really do want to recover the MS windows or MS windows files then plan to run recovery. Then, this will go back from the start and this will be a long process ahead.
Which is to do a dual booting. installing again the Linux operating system after the MS windows recovery. Here you should plan first what is to be done then proceeds to the next process. This is really a mess. Doing a recovery is very impossible but it is possible due to the recovery part of the storage. Here you can maybe recover the MS windows but the MS Windows files is a rare thing to be recovered. It might be recovered but only few of them. So regards and cheers.

---

