---
title: "Reading windows files in ubuntu ?"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by bikinguy77388 on 2008-06-01
Hi All,

I am using ubuntu on a virtual drive in win2000 sevpak4.
I would like to be able to read windows files in ubuntu.
I have read that if I have fat32 file system installed I should be able to not only read but modify them also.

But first things first how do I accomplish this.

Thanks in advance,
bikinguy

---

### Post by Prospero2006 on 2008-06-01
```

sudo apt-get install smbfs

```

On windows, right click the folder you want to share and choose sharing.
Make the folder accessible to everyone on the network. Windows will warn
you that it is unsafe. 

Now, on the linux do this 

```


smbclient -L ip_addy_of_windows


```

You'll see a list of shares available on your windows box.
Let's say the share name is my_folder.
Create a folder on linux called /mnt/sambafolder
then do this
```

mount -t smbfs //ip_addy_of_windows/myfolder /mnt/sambafolder

```

This should mount the windows folder at /mnt/sambafolder.

I hope that helps.

---

### Post by bikinguy77388 on 2008-06-01
Thanks Prospero
I guess using a virtual drive as opposed to a seperate partition the same rules apply.

Bikinguy

---

