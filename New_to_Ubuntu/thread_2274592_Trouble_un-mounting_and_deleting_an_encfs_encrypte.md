---
title: "Trouble un-mounting and deleting an encfs encrypted directory"
date: 2015-04-20
forum: New to Ubuntu
---

### Post by wizrddreams on 2015-04-20
Hello. 
I was toying around with encfs and I was hoping to create an encrypted folder to store passwords and username's in. However I have screwed something up and I am unable to un-mount the one of the encrypted folders I made. 

I ran this command:

```
encfs ~/Desktop/encrypted_test ~/Desktop/test
```

This created two folders on the Desktop (both of which had Lock and X symbols on them).

I couldn't access them, with a few methods, so I decided I wanted to delete them. 

I used ```
rm -rf
``` on the encrypted_test directory and that was deleted. But now I am stuck with the test folder on my desktop. 

When I open my files I see that test is mounted but I can't un-mount it from the menu. I get this error "Unable to unmount test" "umount: /home/kblawlor/Desktop/test is not in the fstab (and you are not root)"

I am all screwed up here and a complete noob with this program. Any guidance would be greatly appreciated!

I think what may have happened is that I created two encrypted directories somehow, and managed to mount one but not the other.

In order to unmount the "test" folder on the Desktop I ran:
```
fusermount -u ~/Desktop/test
```

The output of which is
"fusermount: entry for /home/kblawlor/Desktop/test not found in /etc/mtab"

Please help!
The goal is to unmount and delete.

---

### Post by wizrddreams on 2015-04-20
Alright well this was an easy one to fix and silly on my part.
Simply restarting the computer forced the file to un-mount. 

Then ```
sudo rm -rf ~/Desktop/test
``` properly deleted the folder.

---

### Post by Geoffrey_Arndt on 2015-04-20
I really like the "gnome-encfs" manager.   Have to load a PPA to get the deb file, but it seems to simplify managing encrypted files.   Works great for dropbox.

---

