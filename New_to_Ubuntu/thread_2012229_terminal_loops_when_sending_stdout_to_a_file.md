---
title: "terminal loops when sending stdout to a file"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by emekadavid on 2012-06-28
I have a script (find attached as casescript2.txt) that has a decision construct and accepts user input but on the terminal i had to prepend the stdout to a file while the script executes, thus:
```
./casescript  >>examplefile
```as the script executes the terminal enters a loop when user input is needed since stdout does not show on the terminal but goes to the file. how do i take the terminal out of this loop gracefully. 
tanx

---

### Post by papibe on 2012-06-28
Hi emekadavid.

You could use the command 'tee' to double every thing in the standard output to a file:
```
./casescript  |  tee -a examplefile
```
The '-a' option is to append to the file (equivalent to >>).

Hope it helps.
Regards.

---

### Post by emekadavid on 2012-06-29
> **papibe said:**
> Hi emekadavid.

You could use the command 'tee' to double every thing in the standard output to a file:
```
./casescript  |  tee -a examplefile
```The '-a' option is to append to the file (equivalent to >>).

Hope it helps.
Regards.
my problem is that the terminal halts when it has to read USERINPUT. see the attached script for yourself. My worries are not about the terminal command but why the script does not go to completion and why terminal halts. tanx

---

### Post by papibe on 2012-06-29
I tested your code with 'tee' and it works. No loop or halt.

Regards.

---

### Post by emekadavid on 2012-06-29
> **papibe said:**
> I tested your code with 'tee' and it works. No loop or halt.

Regards.
thanks. happy about that. will try it when i resolve some other problem which i just posted. 
lol

---

### Post by emekadavid on 2012-06-29
> **emekadavid said:**
> thanks. happy about that. will try it when i resolve some other problem which i just posted. 
lol
tee -a worked.
tanx a million

---

### Post by sisco311 on 2012-06-29
> **emekadavid said:**
> my problem is that the terminal halts when it has to read USERINPUT. see the attached script for yourself. My worries are not about the terminal command but why the script does not go to completion and why terminal halts. tanx

It just waits for your input. You don't see the prompt because the stdout of the script is redirected to a file. ;)

---

