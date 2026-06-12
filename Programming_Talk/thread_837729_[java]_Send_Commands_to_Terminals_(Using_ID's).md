---
title: "[java] Send Commands to Terminals (Using ID's?)"
date: 2008-06-22
forum: Programming Talk
---

### Post by Pyro.699 on 2008-06-22
Hello,

I do not know if this is possible and the idea (for me) is somewhat hard to word so i will try my best to do so. I have created a program in java that makes use of the Gnome Terminal; the script has the capability to send keystrokes and mouse movements. The main process of the script is to open a URL (using methods within the java language) retrieve image urls and send those URLS to several text files. There is a maximum amount of 20 text files and the number of image urls added to each file is the same for each file (take the total number, divide by 20 and you have how many you need to create 20 files). What im looking to do is remove the process that involves the keystrokes because this prohibits me from using my computer while the script is running. Is it possible for me to reteive the id of a terminal and send commands that way? an example command would be *gnome-terminal -id <some id> -e <my command> --tab-id <tab #?>*. So here is a basic rundown of the scripts process:

[quote=MyScript.java]
1. Opens terminal
2. Gets images
3. Creates text files

4. sends 3 commands to terminal
4a. wget -x -i input[<id of tab>].txt --directory-prefix=<my path>
4b. touch finished[<id of tab>]
4c. exit
(Once wget finishes it will create the file and then close that tab, this is how i can tell if wget has finished downloading all files)

5. Open new tab <Alt><f> then <b>

6. Repeat steps <4> and <5> 20 times
[/quote]

Is it possible to do all of that without using any keystrokes.

Thank you very much for any help and i would be glad to elaborate if there is anything unclear.
~Cody Woolaver

---

### Post by NormR2 on 2008-06-22
Is there another way you could do this using the Process class?

---

### Post by Pyro.699 on 2008-06-22
I would prefer to have everything run in the terminal just because of how easily it runs. In the future once i learn the GUI aspect of java i plan to make it 100% java and remove the terminal all together, but for now this is how i would like to have it run.

On a side note, im not too fimilar with the process class' at all so if someone is planning on posting an answer could you please go throgh in detail for someone whos new to the idea of using processes. The idea i have in my head is to run a command like *Terminal.send(idNumber, "My Command");*.

Thanks again
~Cody Woolaver

---

