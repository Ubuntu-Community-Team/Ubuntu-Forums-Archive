---
title: "Can I repartition my drive so windowsxp stays intact?"
date: 2008-10-27
forum: New to Ubuntu
---

### Post by joesmith1234 on 2008-10-27
I don't want to do a fresh install of windows... I want to keep it as is.

But I want to add ubuntu to this machine.

I was under the impression that a partition would format the entire drive.  Am I wrong?





Also, does Ubuntu come with an OS juggler so I can use select my OS at system boot?

Thanks.

---

### Post by bodhi.zazen on 2008-10-27
Yes, it is *fairly* easy.

1. back up any data you do not want to lose (just in case)

2. Defragement your Windows.

3. Boot the Ubuntu CD.

4. Resize your Windows partiton to make room for Ubuntu.

5. Install Ubuntu.

Take care to understand linux partitioning so you do not over write Windows.

[HowTo: Partitioning Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=282018") 

There are a number of how-to's with pictures

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

    [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by AndyCooll on 2008-10-27
Yes, you are wrong!

Ubuntu will by default format the entire hard-drive. However when you do the Ubuntu install _don't_ just accept the default options. At the partitioning section choose "manual". Here you can then choose from a range of options such as just using the free-space available, resize partitions etc.

Make sure you make a backup of all your important files first.

And thankfully you had Windows installed first, for Ubuntu handles other OS's much better. It will detect that Windows is already installed and add it to the startup menu so that you have the option which OS to boot into.

:cool:

---

