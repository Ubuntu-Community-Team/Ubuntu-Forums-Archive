---
title: "Install Alongside is missing from the installation menu"
date: 2012-02-21
forum: New to Ubuntu
---

### Post by ehernan3 on 2012-02-21
Hi,
   Although I could not find the solution here 'in time', I solved it and I wanted to share my solution. Maybe someone already posted it and I couldn't find it.

   When attempting to install Ubuntu 11.10 on a machine with Windows(see specs below), the installation process did not show me the "Install alongside" option. The screen I saw is the same as the one shown here: [http://ubuntuforums.org/showthread.php?t=1927748&highlight=install+alongside](http://ubuntuforums.org/showthread.php?t=1927748&highlight=install+alongside)

   The only option I thought I had was to use "Something else", which is not only confusing, but I could not find documentation on it; I only found command line information, which I couldn't follow for something as simple as "install alongside".

   I decided to boot into Windows and look at partitions there in order to decipher what the "something else" option was telling me. I found a Media Direct partition. Having installed and partitioned Windows OSs a few times, I was perplexed by this one(wife's old laptop, OEM installation). Some research quickly revealed some background on why this partition was there, and I decided I didn't want or need this, and that it was interfering with the Unbuntu installation. When I deleted this, I also made sure the remaining space was unallocated. In hindsight, I think the issue was that there was no unallocated space period. If that was the case, then I overlooked the large flaming installation instructions regarding this.

   When I rebooted from disc and tried to install Ubuntu again, lo and behold, the "install alongside" option was there! The installation is now proceeding according to what's been documented.

   I wanted to share this because I had no success finding information to help me  sort this out. It would be nice to have this in the installation documentation(what to do if the "install alongside option is missing"), especially for noobs like me. Of course, I may not be searching for the right terms, but the solution was simple and here it is.

   You may already know that Windows XP does not have partition resizing built in, although you can buy software to do this. If I had installed Windows myself, I wouldn't have allowed Media Direct to do this(and I would have limited the size of the Windows partition anyway). The goal for this installation(my first Linux install ever) was to do it quickly and simply so I could test drive this Linux thing without booting from the CD all the time. If I love it, I'm going to install it 'the right way'.

Cheers,
Ed
Dell Inspiron 1525
Windows XP Pro

---

### Post by Mark Phelps on 2012-02-21
Glad you solved it, but the lack of an "alongside" option is really due to very different problems ... which require very different solutions.

In your case, removal of a partition solved the problem because, in all likelihood, your PC alread had the maximum number of primary partitions allocated -- preventing the installer from creating any more.

Since the removal of ANY partition is going to cause anything from loss of data to inability to boot, it's understandable that the installer is NOT going to offer an option to do this.

But, I agree, the reasons for NOT continuing with the installation could be better presented to the person attempting the install.

---

