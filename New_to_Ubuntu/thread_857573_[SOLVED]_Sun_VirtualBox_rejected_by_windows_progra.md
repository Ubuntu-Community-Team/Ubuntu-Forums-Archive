---
title: "[SOLVED] Sun VirtualBox rejected by windows programmes"
date: 2008-07-12
forum: New to Ubuntu
---

### Post by nuddernuby on 2008-07-12
Have installed VirtualBox on 8.04 host and loaded both XP and Mandriva on two virtual machines - the latter largely for curiosity's sake.

Windows programmes (in this case games) install normally but when executed generate an error message that says that the operating system is incorrect and please to upgrade (!!) to Windows 2000 or higher.

What needs to be adjusted to make the Windows programmes believe that they really are in a correct environment? Any advice will be appreciated.

---

### Post by hyper_ch on 2008-07-12
what programs?

---

### Post by nuddernuby on 2008-07-12
The Box is set up for the the kids to play windows games within the Ubuntu environment. The games loaded included Command and Conquer, Sims2, Empire Earth, etc.

---

### Post by hyper_ch on 2008-07-12
I guess those require directx and vbox does not support 3d acceleration

---

### Post by nuddernuby on 2008-07-13
Genau. 
DirectX was installed during setup.
Does this mean the end of the road and a return to dual boot?

---

### Post by hyper_ch on 2008-07-13
wine runs up to directx 8.... you might want to try that...

---

### Post by Dedoimedo on 2008-07-13
Hi,

Depends on what XP version you got. SP2 and on, you WILL have problems with older games. You might try XP without any SP.

Furthermore, for older games, you can also try DOSBox - the best there is for DOS-based games, including network support.

Dedoimedo

---

### Post by bumanie on 2008-07-13
Virtualbox does not have 3d acceleration and uses the stable, but 'basic' vesa graphics driver. Anything that needs 3d acceleration will not work in virtualbox. You must appreciate that vm's were initially designed for corporate use for cutting costs by virtualising severs etc. - 3d acceleration is not high on the list of features for servers.

---

### Post by nuddernuby on 2008-07-13
Thank you for the feedback.
Judging by the ingenuity of the opensource community, I suppose it won't be long before this will also become possible. In the meantime, we'll use something different.

---

