---
title: "BADSIG: (cant seem to fix it)"
date: 2012-08-30
forum: New to Ubuntu
---

### Post by Hammer3344 on 2012-08-30
Due to me having 2 laptops, I have neglected the one that I am currently on when it came to updates and pretty much any other function that I needed. I now have a need to install the rar and unrar packages to access some files, but cant until I run the apt-get update.
When running update I am prompted with this output.

```
W: GPG error: http://archive.canonical.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```At which point I ran
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 40976EAF437D05B5  

```and got
```
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1


```Previously I had 3 keys that came up as "BADSIG" but the issue seemed to be fixed by resetting the defaults in the update manager. some of the other commands I ran due to other errors that I encountered (issues ranging from being unable to access the update manager to being unable to run apt-get update without getting a header issue)

for the broken files I ran
```
sudo apt-get update -f
```and for no headers I ran
```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```bringing me back to the same spot every time with no change in the overall output (minus the broken header part)
Very annoying, and it feels like a never ending loop. What are some other options that I can try?

Thanks in advance for your assistance!

Additional steps:
I have continued doing research in the hopes that I will be able to solve this issue on my own. I tried to remove the key from the key ring in the hopes of re-adding it to the keyring. However, I found the syntax commands for the gpg manager and ran the following command.
```
sudo apt-key adv --refresh-keys --keyserver keyserver.ubuntu.com

```and got the following output
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.Lu9DCH6u7h --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --refresh-keys --keyserver keyserver.ubuntu.com
gpg: refreshing 5 keys from hkp://keyserver.ubuntu.com
gpg: requesting key 437D05B5 from hkp server keyserver.ubuntu.com
gpg: requesting key FBB75451 from hkp server keyserver.ubuntu.com
gpg: requesting key 3E5C1192 from hkp server keyserver.ubuntu.com
gpg: requesting key F59EAE4D from hkp server keyserver.ubuntu.com
gpg: requesting key D66B746E from hkp server keyserver.ubuntu.com
gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key FBB75451: "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" 28 new signatures
gpg: key 3E5C1192: "Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: key F59EAE4D: "Launchpad PPA for NoobsLab" not changed
gpg: key D66B746E: "Skype Technologies S.A. <info@skype.net>" not changed
gpg: Total number processed: 5
gpg:              unchanged: 4
gpg:         new signatures: 28
gpg: no ultimately trusted keys found

```which did not fix the issue either. Still getting the original BADSIG output (listed at the top)
I also ran the update trustdb command
```
 sudo apt-key adv --update-trustdb

```and got the following output
```
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.gAY5Nd4mnM --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --update-trustdb
gpg: no ultimately trusted keys found
```I have tried rebuilding the keydb-caches
```
sudo apt-key adv --rebuild-keydb-caches
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.B3f6RZNN57 --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --rebuild-keydb-caches
gpg: caching keyring `/etc/apt/trusted.gpg'
gpg: 5 keys cached (95 signatures)

```ran apt-get update and still the same thing.
Going to continue working on this, but I am reeaaaaly open to suggestions at the moment. Thanks in advance for any feedback you can offer.

Final edit:
I was able to download the rar/unrar packages that I needed, however the keysig issue is still there. I have tried numerous steps and have failed on all of them...I will check back shortly to see if there is any other assistance.

Thanks again in advance!

---

### Post by coldcritter64 on 2012-08-30
On Oneiric the only repo I have with archive.canonical.com in is the partner repos. I searched the /etc/apt/sources.list in gedit to check.

Try deselecting them (the partner repos) in software sources before running the update. 
Then rerun the update without them. 

If the update goes through, any software from the partner repos won't be updated if you have any applications from there installed. Might give you a bit of "breathing room" while looking for a fix. I'm not sure about how to deal with the BADSIG error though.  Good luck.

---

### Post by papibe on 2012-08-30
Hi Hammer3344.

Are you using any caching proxy? If so, you may want to clean the cache in case the saved sources, or packages, are corrupted.

Just a thought.
Regards.

---

### Post by Hammer3344 on 2012-08-31
once I get a chance I will take a look at those suggestions. Certainly brought some new ideas to the table. thanks guys!

---

