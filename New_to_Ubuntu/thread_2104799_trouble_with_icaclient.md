---
title: "trouble with icaclient"
date: 2013-01-14
forum: New to Ubuntu
---

### Post by Old Jimma on 2013-01-14
Hi Community:

Many times when I install software, for some reason it wants to install icaclient. 

On every occasion, I get the error:

> E: icaclient: subprocess installed post-installation script returned error exit status 2

I dont understand this.

How can I get icaclient installed sucessfully?

The suggestions at: [https://help.ubuntu.com/community/CitrixICAClientHowTo]("https://help.ubuntu.com/community/CitrixICAClientHowTo")

did not work for me.

Thanks,
Old Jimma from the Old Country

---

### Post by Steeperton on 2013-01-14
I presume you're using 64bit Ubuntu?

1. Install the .deb and let it fail
2. Edit /var/lib/dpkg/info/icaclient.postinst
3. Replace the line that says ```
echo $Arch|grep "i[0-9]86&quot; >/dev/null 
```with ```
echo $Arch|grep -iE "x86_64" >/dev/null
``` 
4. Run dpkg --configure icaclient

Taken from [http://forums.citrix.com/thread.jspa?threadID=306353&tstart=0](http://forums.citrix.com/thread.jspa?threadID=306353&tstart=0)

---

### Post by spynappels on 2013-01-14
You also need to ensure libmotif4 is installed for it to work correctly:
```
sudo apt-get install libmotif4
```

---

### Post by Old Jimma on 2013-01-15
Hi Steeperton:

the line you recommended I replace did not exist in that file precisely as you specified.

I found one that was quite similar, however, and made the replacement.

After that I did the

dpkg --configure icaclient

and got the error message:

> Setting up icaclient (12.1.0) ...
/var/lib/dpkg/info/icaclient.postinst: 2983: /var/lib/dpkg/info/icaclient.postinst: Syntax error: Unterminated quoted string
dpkg: error processing icaclient (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 icaclient


what should I do now?

Thanks,
Old Jimma

---

### Post by Steeperton on 2013-01-15
I've just checked my icaclient.postinst file, and line 2648 says this:
```

	echo $Arch|grep -E "i0-986|x86_64" >/dev/null

```

Which isn't quite the same as I had thought I'd made it... But it works!

You could try that (then reconfigure again afterwards).

Which OS (32 or 64 bit?) and which ICA Client are you using (link to the download?)

Thanks,

---

### Post by Old Jimma on 2013-01-15
Hi Steeperton:

Changing that line to your latest suggestion returned no errors when I ran

> 
dpkg --configure icaclient

I'm not sure exactly what this fixes. Seems obscure but important.

Could you explain it to me?

Thanks!
Old old Jimma, The Eldest
From the Ancient Country

---

### Post by Old Jimma on 2013-01-17
Steeperton's last suggestion to the problem of broken ica client worked. This thread is solved.

---

### Post by Steeperton on 2013-01-17
> **Old Jimma said:**
> 

Could you explain it to me?


Not really! :p

I'm not sure what's it doing - it appears to be passing anything with "86" to null (i.e. deleting it), but as we're on 64 bit, it was running into the errors. Adding the "x86_64" into the argument, and it also passes the 64 stuff to null.. Why it needs to do that, I've no idea.

I also think there's a typo in there, it should be "[0-9]86" (to ensure it also works for 32 bit), but as it works fine for me, I don't particularly want to amend it back again!

---

