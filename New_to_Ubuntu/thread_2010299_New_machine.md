---
title: "New machine"
date: 2012-06-25
forum: New to Ubuntu
---

### Post by Penfold1971 on 2012-06-25
i've just built a new PC - the first time I've had the courage. It has an Intel Core i7 2600k processor.

Should I download the 64-bit or 32-bit version of 12.04?

The machine will be devoted exclusively to running Folding@home continuously, nothing else.

---

### Post by dniMretsaM on 2012-06-25
Unless you know you need something that has a bunch of problems on 64-bit systems (which are fairly rare nowadays),  go for 64-bit. Installing 32-bit wouldn't harm anything, though.

---

### Post by Cheesemill on 2012-06-25
Go for the 64-bit version.

Bear in mind that if you have a GPU that you wish to use for folding, then this feature is only available for Windows. If you are only going to be folding with the CPU then Ubuntu is a good option.

---

### Post by Curtis6767 on 2012-06-25
Looks like folding@home is a 64bit deb file and your processor is a 64bit processor so 64bit Ubuntu is what you're looking for.

Once you get 12.04 installed, then install Gdebi through the Software Center. Then after you have downloaded folding@home to your downloads folder just right click on the file and select Gdebi from the drop down menu. 

GL

---

### Post by Cheesemill on 2012-06-25
> **Curtis6767 said:**
> Once you get 12.04 installed, then install Gdebi through the Software Center. Then after you have downloaded folding@home to your downloads folder just right click on the file and select Gdebi from the drop down menu. 

No need, you can choose to install a .deb file directly with Software Center when Firefox kicks of the download.

---

### Post by Penfold1971 on 2012-06-25
Thanks everyone.

I haven't put a graphics card in - it'll run on CPU.

When it says 'amd64' in the filename for the download, is it still OK for Intel? Possibly a daft question, but I am ultra cautious as a total untutored newcomer.

---

### Post by sudodus on 2012-06-25
> **Penfold1971 said:**
> Thanks everyone.

I haven't put a graphics card in - it'll run on CPU.

When it says 'amd64' in the filename for the download, is it still OK for Intel? Possibly a daft question, but I am ultra cautious as a total untutored newcomer.
Yes, still OK

---

### Post by ranger1021994 on 2012-06-25
64 bit would be helpful if you install RAM more than 4GB...but still 64 is preferable for long term...
:)

---

### Post by nipunshakya on 2012-06-25
Looking at your computer's spec, 64 bit works as a charm... go for it man...

---

### Post by Paqman on 2012-06-25
> **Cheesemill said:**
> 
Bear in mind that if you have a GPU that you wish to use for folding, then this feature is only available for Windows.

Is that a Folding thing? Seti@home handles CUDA fine.

Another +1 to the 64-bit recommendation. Number-crunching like this will be significantly faster on 64-bit.

---

### Post by Penfold1971 on 2012-06-25
Many thanks to you all. Success. Downloaded, installed and everything is looking good.

---

### Post by Cheesemill on 2012-06-25
> **Paqman said:**
> Is that a Folding thing? Seti@home handles CUDA fine.
It's just a folding thing, no-one has written a Linux GPU client yet.

---

### Post by nipunshakya on 2012-06-25
Glad to know you are up and working.. Goodluck

---

