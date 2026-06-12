---
title: "Running a Script upon Logout in Unity"
date: 2015-03-24
forum: Programming Talk
---

### Post by squirrel2003 on 2015-03-24
Hi, i am trying to get a .sh script executed each time i lock my screen in ubuntu using the unity desktop.
I successfully got it executed upon logout by editing the session-cleanup-script dependancy line in to the 50-unity-greeter.conf  file.
Will the script be executed upon locking the screen that way or do i have to change something?
Thanks in advance.

---

### Post by ofnuts on 2015-03-24
I don't know Unity, but in KDE you can set up notifications and what happens when they trigger (play a sound, run a script...). Among the possible notifications I have a "Screen locked" in the "Screen saver" category. I would be surprised if you hadn't got the same in Unity.

---

### Post by squirrel2003 on 2015-03-26
> **ofnuts said:**
> I don't know Unity, but in KDE you can set up notifications and what happens when they trigger (play a sound, run a script...). Among the possible notifications I have a "Screen locked" in the "Screen saver" category. I would be surprised if you hadn't got the same in Unity.

I don't know if this option exists in unity enviroment, there are notification in the desktop enviroment fe i find the thunderbird notification for new mails quite annoying, the mail sign turning blue would be enough for my purposes but i never looked deeper into this.

Afaik logout and lock are two different things so i will have to change the location of the session greeter script script but i don't find any solved threds regarding this issue on using google search.
Furthermore i was wondering if such a RAM cleaning script would work on android too and if it would effectively clean the memory of encryption keys in that case since encryption afik works differently in android.

---

### Post by ofnuts on 2015-03-26
There are many concepts behind "notifications". The quick popup above the system tray is one of them (that also exist in KDE), but here I'm talking about are "events" to which you hook anything.

Cleaning you RAM on logout is one thing (all your processes will be killed anyway) but on a screen lock your processes continue to run and some may need the keys.

---

### Post by squirrel2003 on 2015-03-31
I am trying to achieve to get RAM cleaned before i lock the screen to prevent boot attacks while cheese webcam is recording.
So what you are saying is that this is not possible because the system encryption keys (I am using ubuntu FDE on one  system and an encrypted home directory on the othe) are in use while cheese is recording?
In that case i will have to work with tresor or  twitch streaming although tresor seems quite hard to setup and  streaming is risky because the connection could theoretically break down or the modem which is wired in my case.

Tresor would be the best solution for sure as i see it but i could not find any tutorial that explains how to set it up noob friendly.

---

### Post by ofnuts on 2015-04-01
The real question is which bits of the RAM you want to clean...  If it's the one in unallocated/buffers then yes, but you can't clean the RAM used by running process, so you RAM-cleaning is going to be incomplete. Unless said process are guaranteed to not use any of your keys, or obliterate them in RAM once they have been used (but if they do so, you won't find them in in the unallocated RAM either :)). 

... and all you keys come from some mass storage which is likely a lot easier to access.

---

### Post by squirrel2003 on 2015-04-28
> **ofnuts said:**
> The real question is which bits of the RAM you want to clean...  If it's the one in unallocated/buffers then yes, but you can't clean the RAM used by running process, so you RAM-cleaning is going to be incomplete. Unless said process are guaranteed to not use any of your keys, or obliterate them in RAM once they have been used (but if they do so, you won't find them in in the unallocated RAM either :)). 

... and all you keys come from some mass storage which is likely a lot easier to access.

In my case i want to clean the encryption key of the system partition (i am using standard LUKS LVM encryption provided by the installer DVD or manually setup) out of RAM to prevent someone from restarting the system and implementing a boot attack in order to gain access to my system while i am afk.

The processes that i would have running on my system while being away  are a webcam program and transmission plus maybe some remote control  program but since the partition is in a decrypted state while in use  none of those programs should be writing my system encryption keys into  RAM so i guess it should be possible to overwrite the remnants of the system encryption keys using sdmem?

I realised that the screen locking password, which is in my case the same as the sudo password could also  be a vulnerability.
I don't know if it is possible for an attacker to remove the RAM chip, cool it, read out the sudo password and reinsert it to the computer then simply log in by entering the extracted password and gain access to the system this way without the need of the system encryption password but i guess that the sudo password is  located in the unallocated region of the RAM right before locking the screen in any case which makes it overwritable by sdmem?

---

### Post by ofnuts on 2015-04-28
Your processes have no knowledge of the encryption, to it is unlikely that their own memory contain the decryption key.

From my understanding of LUKS, the encryption key should be somewhere in kernel space but if you obliterate it you lose access to your LUKS partition (in the best case...). And this key is used until after all user processes are terminated during shutdown (flushing buffers to disk), so there is no way you can wipe it out with anything that runs while the LUKS-enabled system is running.

Going full paranoid mode: your key is rather easy to obtain... get hold of your machine, replace the kernel image (these are not on the encrypted partition) by one that also stores the key in some hidden place (steganography techniques), or since it knows your key, adds a known key in one of the ke*****s. Then wait for you to check the machine, reboot it, and re-enter the key. Come back a while later and get the machine again,  with the encrypted partitions, and the key :). Better take a MD5 hash of the files in your /boot and check these before rebooting.

---

### Post by squirrel2003 on 2015-04-28
> Your processes have no knowledge of the encryption, to it is unlikely that their own memory contain the decryption key.

From my understanding of LUKS, the encryption key should be somewhere in  kernel space but if you obliterate it you lose access to your LUKS  partition (in the best case...). And this key is used until after all  user processes are terminated during shutdown (flushing buffers to  disk), so there is no way you can wipe it out with anything that runs  while the LUKS-enabled system is running.


OK, so i looked kernel space up on wikipedia and wikipedia says that it is a part of virtual memory.
Virtual memory is managed by the CPU as far afaik.
So in that case the system encryption keys should not be extractable by a Cold Boot Attack because it targets RAM so i guess there should be no need to wipe those keys anyway as long as there is no method that i don't know of which makes it possible to extract encryption keys from the CPU while in use.

I reread the wikipedia article on cold boot attacks and an interesting part is that it says that the documents that are being worked on while the power is on could reveal the FDE key.



> Going full paranoid mode: your key is rather easy to obtain... get hold  of your machine, replace the kernel image (these are not on the  encrypted partition) by one that also stores the key in some hidden  place (steganography techniques), or since it knows your key, adds a  known key in one of the ke*****s. Then wait for you to check the  machine, reboot it, and re-enter the key. Come back a while later and  get the machine again,  with the encrypted partitions, and the key :smile:. Better take a MD5 hash of the files in your /boot and check these before rebooting.
I don't fully understand that method you are explaining, but from what i understand it has the same effect like a boot sector virus or manipulation of the bootsector.

---

