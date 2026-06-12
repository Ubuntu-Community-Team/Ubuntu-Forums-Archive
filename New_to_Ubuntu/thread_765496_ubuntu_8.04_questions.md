---
title: "ubuntu 8.04 questions"
date: 2008-04-24
forum: New to Ubuntu
---

### Post by dtrot55 on 2008-04-24
I am noob to Ubuntu still unfortunately and i have 7.10 installed. Here are some questions i have.

Will drivers from 7.10 work in 8.04 if there are no 8.04 drivers out yet? I'm still getting the hang of installing drivers so if they have changed anything it will take me forever to learn it all again.

Software: I had a hard enough time getting Whine to work in 7.10...do i have to wait for a new version or are older version compatible?

If anyone could fill me in on why it would be better to switch to 8.04 it would be much appreciated.

Also if someone could help me with my hardware and find drivers for them that would be nice to.

Sound Blaster X-FI Fedlity Plat Sound Card
Nvidia 8600GT Video Card
Brother MFC420CN Printer

I know it's noob...i hit myself everytime i have to make one of these post..but you have to start somewhere.

Thanks

---

### Post by rouge568 on 2008-04-24
1) Drivers should still work from 7.10, but you should always use the most up to date everything.

2) Wine is in the repositories and very easy to set up. Just type 'sudo apt-get install wine' into a terminal.

3) There are quite a few benefits of 8.04 over 7.10. It has a better default application base, including more up-to-date applications. (Firefox 3 and Open Office 2.4 are good examples) It has a newer kernel, which means it will be faster (especially booting!) and will have support for a lot more hardware. Anything newer will also be faster, have more features, and be more secure. In addition, not personal data will be lost if you do it via the update-manager. By all means, go to 8.04.

4) I'm don't have experience with printer or sound card drivers, but your nvidia card should be supported. In 8.04, go to System>Administration>Hardware Drivers and enable everything there. (In 7.10 it is called the Restricted Drivers Manager)


Let us know how it goes!

---

