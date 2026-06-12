---
title: "Deleting files permanently using a GUI?"
date: 2012-05-01
forum: New to Ubuntu
---

### Post by nullified_nostalgia on 2012-05-01
I've read countless threads about permanently deleting files and the answer always seems to be shred or secure-delete.  Those things require typing in the name of the file in the terminal.  What if it was several hundred or several thousand files?  At that point typing their names is not an option.

If the files are in a folder and you shred the folder, does it just shred the directory name or does it shred all the files that are in the folder as well?

On windows there's ccleaner, which with a simple GUI selection allows doing 7 or 35 pass overwrites of the files in the recycle bin.  Is there anything with a GUI like this for linux?

I've also read suggestions about encrypting your directories, but if the password was obtained somehow the encryption does no good.  Then there's the option that something goes wrong and you've locked yourself out of all your files, so encryption doesn't sound like a good solution to me.

---

### Post by pqwoerituytrueiwoq on 2012-05-01
maybe a nautilus script could do it 

there are wild cards for terminal commands 
ls /usr/bin/g*

---

### Post by nullified_nostalgia on 2012-05-01
I found a program called BleachBit that does exactly what I'm wanting.  I learned quite a bit about securely deleting files from it's documentation at [http://bleachbit.sourceforge.net/documentation/shred-files-wipe-disk](http://bleachbit.sourceforge.net/documentation/shred-files-wipe-disk)

I read in the documentation of another program that one pass isn't enough even though bleachbit claims it is (it even referenced bleachbit), but what the bleachbit documentation says actually make sense, whereas the documentation on the programs that do 3, 7 or 35 passes don't seem to have any hard evidence to back up their claim that multiple passes are needed.
[]("http://bleachbit.sourceforge.net/documentation/shred-files-wipe-disk")

---

### Post by Cheesemill on 2012-05-01
No need to do multiple passes with random data like most people suggest. Just overwriting once with 0's will prevent any recovery.

---

