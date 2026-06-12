---
title: "LaTeX + eps file edited in Windows hangs in Linux"
date: 2007-06-06
forum: Programming Talk
---

### Post by krypto_wizard on 2007-06-06
Hi,

I am not sure if this is the right place to post here but since I was using LaTeX and Matlab for preparation of my document in Feisty, I thought of asking my problems to code gurus.

I am using Matlab in Windows to generate .eps files. I then use those files in Adobe Illustrator to edit and save back again as .eps files.

Then I use these figures to create a document using LaTeX in Feisty, the LaTeX file takes nearly 3-4 minutes to compile and the whole system becomes unstable. If I click on Firefox, it opens after 5 minutes, I can't even open terminals. I later figured out that the eps files created in windows are making in unstable and I compiled LaTeX file again and it did it in 6 seconds. 

Now, my question is how do I use the figures which were modified in Windows to create the doc in LaTex seamlessly.

Any help would be appreciated.

Thanks

---

### Post by krypto_wizard on 2007-06-07
any answers ...... ?

---

### Post by WW on 2007-06-07
How big is the eps file after you edit it with Illustrator?  Can you attach an example here?

---

### Post by hod139 on 2007-06-07
You can try running eps2eps and seeing what happens.

---

### Post by WW on 2007-06-07
Your problem might be related to the bug reported here: [https://bugs.launchpad.net/ubuntu/+source/kdegraphics/+bug/110765](https://bugs.launchpad.net/ubuntu/+source/kdegraphics/+bug/110765)

---

### Post by krypto_wizard on 2007-06-08
Thanks for all the responses. 

I remove ps-esp and its dependencies and I get rid of the problem. I don;t know hows and why of the problem but it worked for me.

Thanks once again.

---

### Post by rplantz on 2007-06-08
I don't know if this is useful information to you, but I use OpenOfficeDrawing to create drawings and export them as .eps files. I save the .odg file in case I need to modify my drawing. I often need to use an editor (I use gedit) to modify the values in
```

%%BoundingBox: 0 0 332 188

```
in order to get a good placement in my document.

---

