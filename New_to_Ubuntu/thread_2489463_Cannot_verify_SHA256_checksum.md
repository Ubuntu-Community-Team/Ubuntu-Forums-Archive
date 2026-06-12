---
title: "Cannot verify SHA256 checksum"
date: 2023-07-31
forum: New to Ubuntu
---

### Post by tron100 on 2023-07-31
1. Perhaps other variants of this question have been answered, but as far as I can tell so far mine is unique.  I have not been able to find any answer online. 
2. As a new user interested in Ubuntu I downloaded Ubuntu from the official ubuntu.com website. 
3. I did so only a few days ago in July 2023. Ubuntu version 22.04.2. 
4. After using Rufus (as suggested online) to get it onto my 64GB 3.0 Sandisk thumbdrive, and following advice online about which options to choose in Rufus, the thumbdrive was ready. 
5. I put the thumbdrive into my second computer that it was meant for. 
6. After it apparently uploaded and worked successfully, I went to an article that describes security measures every Ubuntu user should take. 
7. One of the items on that list is to "verify the Ubuntu ISO image checksum". 
8. I was able to follow directions enough to find on the ubuntu.com download page the SHA256 Checksum, which begins with "b98...". 
9. However, when I tried to put in commands (recommended online) into the terminal of my freshly installed Ubuntu, they would not work. 
10. Some commands unrelated to checksum worked fine, but none related to checksum. 
11. To those, the terminal would consistently respond with: "No such file or directory" 
12. (Yes I verified that I spelled the commands correctly, and yes there had been multiple computer resets). 
13. Therefore I tried to download a graphical ui option (suggested online_ called "hgk..." something.  (At the time I put in the exact name). 
14. However, despite being connected to the internet, no results but a spinning wheel were even given in the Ubuntu Software app. 
15. I went to the ISO image downloaded originally on the first pc, and there is no folder that I could identify that has the answer I was looking for. 
16. However, there was a file called "md5sum".  Even though md5sum is not SHA256, I opened it anyway. 
17. Nothing beings with "b98..." in that long list of number strings. 
18. A similar file is located in my thumbdrive that I used Rufus to get the Ubuntu ISO there.  However, that also does not contain any number string that begins with "b98...". (It's probably the exact same file with the exact same info). 
19. I read online that the number needs to match exactly in order to by verified and safe. However, I cannot find the "b98..." number that is listed on the Ubuntu website anywhere. Am I looking in the wrong place? 
20. I re-downloaded the whole thing again in case it downloaded faultily, but same results as above. 
21. What am I missing? 
22. I would really like to use Ubuntu if possible but only if I can make sure it is safe. 

Thank you

---

### Post by Holger_Gehrke on 2023-07-31
Well, in theory the verification step should come before flashing the image to a thumbdrive. You're supposed to use some program to calculate a checksum (it's a lot more complicated than a simple checksum, but serves a similar purpose) for the image file and compare the result to the one stored in the file SHA256SUMS. If you're doing all this on some variant of Linux, there's a tool named sha256sum which on Ubuntu is part of the package coreutils. When you call it with 'sha256sum -c SHA256SUMS' it reads SHA256SUMS and then calculates checksums for all the files in the current directory listed in the file and compares them to the ones stored alongside the file names. On Windows you can calculate the hash value with Powershell by entering 'Get-Filehash TheFileYouWantToCalculateTheHashFor.whatever -Algorithm SHA256' (replace the obvious). You'll have to do the comparing yourself then.

By the way, if you had downloaded Ubuntu by torrent you could save yourself the trouble. Torrents are checksummed for each file, each block and each part of a block and those sums are checked during download. If something doesn't match it gets discarded and the download is repeated. So if your torrent client says a file is downloaded correctly then you can trust that the file is OK.

Holger

---

### Post by tron100 on 2023-07-31
Today shortly after posting this, someone tried to create a Microsoft account with my email address.  What is going on?  

Anyway, I really appreciate the time and effort you took to answer my question.  However, my technical knowledge being less than yours, I'll need a much more thorough step 1, step 2, step 3, etc. kind of explanation than given above.

---

### Post by Holger_Gehrke on 2023-07-31
[LIST=1]
[*]Start the PowerShell from the menu on the Windows machine on which you downloaded the image.
[*]Use the 'cd' command to change to the directory where you have the image.
[*]Enter 'Get-Filehash ubuntu-22.04.2-desktop-amd64.iso -Algorithm SHA256' Wait a moment for the hash to be calculated and printed.
[*]Open SHA256SUMS in Notepad or any other editor you like and compare the checksum listed in the file to the one calculated. 
Alternatively you could enter 'type SHA256SUMS' into the PowerShell, that should show the contents of the file.
[/LIST]

Holger

---

### Post by tron100 on 2023-07-31
Okay this is what I've got so far: 

Windows PowerShell
Copyright (C) Microsoft Corporation. All rights reserved.


Try the new cross-platform PowerShell [https://aka.ms/pscore6](https://aka.ms/pscore6)


PS C:\Users\S> cd
PS C:\Users\S> et-Filehash ubuntu-22.04.2-desktop-amd64.iso -Algorithm SHA256
et-Filehash : The term 'et-Filehash' is not recognized as the name of a cmdlet, function, script file, or operable
program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ et-Filehash ubuntu-22.04.2-desktop-amd64.iso -Algorithm SHA256
+ ~~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (et-Filehash:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException


PS C:\Users\S> SHA256SUMS
SHA256SUMS : The term 'SHA256SUMS' is not recognized as the name of a cmdlet, function, script file, or operable
program. Check the spelling of the name, or if a path was included, verify that the path is correct and try again.
At line:1 char:1
+ SHA256SUMS
+ ~~~~~~~~~~
    + CategoryInfo          : ObjectNotFound: (SHA256SUMS:String) [], CommandNotFoundException
    + FullyQualifiedErrorId : CommandNotFoundException


PS C:\Users\S>

---

### Post by Holger_Gehrke on 2023-07-31
Sorry, I expected you to be familiar with the way 'cd' works in command line interfaces in DOS, Windows and Linux (it's the same ...). You need to give it the directory to change to (or a path of directories). For example if the image is in the Downloads folder inside \Users\S, then 'cd Downloads' would change the working directory to that. Or you could use an absolute path and enter 'cd \Users\S\Downloads'.

And Commands in all shells are very sensitive to misspelling. You probably tried to copy and paste the command 'Get-Filehash' and missed the 'G' at the beginning

And SHA256SUMS is probably not in the current working directory and isn't a command. The command would be 'type' and the filename is something the command is supposed to work on (a parameter).

Holger

---

