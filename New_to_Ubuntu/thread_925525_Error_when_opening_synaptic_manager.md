---
title: "Error when opening synaptic manager"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Dr. House on 2008-09-20
Hi,

When I open the synaptic manager, this error shows up:

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: Couldn't read list of package sources

I think Ive screwed up something a few days ago when adding some repo sites. Thanks.

---

### Post by jualin on 2008-09-20
Maybe if you delete the "medibuntu.list" file the problem might go away. You can do it using the terminal by  > sudo rm /etc/apt/sources.list.d/medibuntu.list And then trying adding the repositories again. What way did you follow to add the repositories?

---

### Post by Dr. House on 2008-09-20
Thanks Jualin. Ive already resolved the problem. I followed one of the old posts. Yup, I removed the medibuntu.list. Apparently that doesnt work anymore. I saw this site  and copy and pasted some commands, it was a tutorial on how to enable and add repositories. Thanks again!

---

### Post by jualin on 2008-09-21
No problem, I am glad you found a solution for your problem. Please mark your thread as solved. Thank you in advance!

---

