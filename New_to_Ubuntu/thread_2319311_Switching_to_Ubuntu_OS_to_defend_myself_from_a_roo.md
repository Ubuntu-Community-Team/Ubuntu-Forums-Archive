---
title: "Switching to Ubuntu OS to defend myself from a rootkit!?! (Help)"
date: 2016-04-02
forum: New to Ubuntu
---

### Post by armon2 on 2016-04-02
Hello Ubuntu community!! This is my first time being here. I just wanted to tell everyone my situation and hopefully reach out to me with your opinions on what I should do? Apparently this computer has been compromised by a third party rogue virus which im guessing is a rootkit. I have reformatted my hardrive back to factory settings twice. However this nasty virus is still lodged deep within my files. Which is understandable, I mean, I have a naga gaming mouse that has specific drivers set up to the accuracy of the mouse. And when I did a factory reset on my windows 8.1 laptop the mouse still works with the same speed and accuracy. So, windows factory reset isn't really that good. Regardless, I know I have this virus in my computer. I am getting established connections when I nestat in the cmd panel from the IP address of a public library here in LA, and other established connections that should not be here at all. To top it all off, I have seen this hacker log into my computer and use my mouse, opening files. This person has FULL access to my computer. Now, I would rather just switch to Linux if it will get rid of this retarded virus. Will this be the case if I do so? I am just assuming, because Linux is coded completely different than windows 8. Which, I'm assuming should be impossible for the virus to work because it would then be communicating with a completely different OS. Am I right???

---

### Post by Bucky Ball on 2016-04-02
Welcome. Windows viruses will have no impact on Ubuntu. Be aware that if you have an infected file on Ubuntu and pass it to a Windows machine the virus will go with it, unless you run some kind of virus scanner in Ubuntu. In eight years I've never done so (but not saying you should or shouldn't ... I did run ClamAV for awhile come to think of it, which is a virus scanner for Linux). 

Also be aware that if you are dual-booting with Windows, Ubuntu will not make any difference to the Windows install. It will not change anything there nor fix any issues you have with Windows.

---

### Post by Ogden on 2016-04-02
Before you nuke Windows, try zapping the rootkit with malwarebytes or something similar:

[https://www.malwarebytes.org/antirootkit/](https://www.malwarebytes.org/antirootkit/)

There are a bunch of other solutions also.  Search for "removing rootkit."

After you clean it out, then install Ubuntu as your second OS unless you are 100% sure you will never need Windows again.

---

### Post by Bucky Ball on 2016-04-02
Or run Windows as a virtual machine if you do using Virtualbox. ;)

---

