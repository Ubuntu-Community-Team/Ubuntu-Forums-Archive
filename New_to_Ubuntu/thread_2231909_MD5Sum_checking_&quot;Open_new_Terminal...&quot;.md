---
title: "MD5Sum checking &quot;Open new Terminal...&quot;"
date: 2014-06-28
forum: New to Ubuntu
---

### Post by iforgetagain on 2014-06-28
OK So I wanted to update my emergency disc which was version 9. So I'm ready to create a new disc and the instructions tell me to check it and say "Open terminal...:" and the rest is all a foreign language to me because i have no idea what terminal.  The person who wrote that up assumed I knew things maybe they don't realise they know and do unconsciously now. 

Can someone tell me key stroke by keystroke, mouse click by mouse click how to do the md5sum and that other check to be sure my download is 100% good? 
Thank You 
IFA

PS
Sigining up was extremely frustrating I spent an hour trying to get onto the forum and only when i just logged out and closed all windows then tried to get on again was I able to.  I know the community is big but that seems a bit ridiculous.

---

### Post by Vladlenin5000 on 2014-06-28
Hi, welcome.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by iforgetagain on 2014-06-28
Thank You Vladlenin5000, But that is the page I am referring to when I say the person who wrote it assumed I knew things they did not realise they had internalised. I stillneed actual instructions for click by click how to do it.    This site is a huge pain to get logged into. It took 5 minutes of logging in and out and closing windows to finally get logged in. EDIT I figured out I need to unblock yahooapis and ubuntu scripts when I log in. One problem solved. :)

---

### Post by Bashing-om on 2014-06-28
iforgetagain; Hi !

I try, and see if I can help. In small baby steps as it were.

1). where is the .iso file downloaded to ?
check:
```

ls -la Downloads

```
Once the location is verified we can then direct 'md5sum' to do the calculation:
With a result something like " 2ceb4a82-1959-42a2-94b8-b7364328d7fa "

OK, then we go to the site where you downloaded the .iso file and see what they say should be the 'md5sum' check value and compare the two. They should be identical.

So far so good ?

---

### Post by iforgetagain on 2014-06-28
Thank You Bashing-Om. I have no idea what to do with that code. I have tried using a cmd window and the page linked with no success. I am using a Vista HP operating system Windows computer to create this Ubuntu live disc 14.04 I am not unfamiliar with computers what loses me is "open a terminal..." If I knew what the heck that was I might be able to figure it out, otherwise what you have posted is also foreign to me.  To answer your question I downloaded it to the desktop  as that is easiest to burn it to disc.

---

### Post by lisati on 2014-06-28
> **iforgetagain said:**
> I am not unfamiliar with computers what loses me is "open a terminal..." 
Hopefully this link will help you get started: [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by Vladlenin5000 on 2014-06-28
> **iforgetagain said:**
>  I have tried using a cmd window and the page linked with no success. I am using a Vista HP operating system Windows computer to create this Ubuntu live disc 14.04

You could/should have said that from the start :lolflag:
And doing a simple Google search with "MD5Sum windows" would get you there instantly. Here's the official Microsoft document about it: [http://support.microsoft.com/kb/889768/en](http://support.microsoft.com/kb/889768/en) (yes, you have to use the terminal as well :grin:). There are also many graphical (and free) apps to do just that.

---

### Post by coldraven on 2014-06-28
I found this video which might help, the utility  AcetoneISO is in the Software Centre.
[http://www.youtube.com/watch?v=5mwDjQUOEBY](http://www.youtube.com/watch?v=5mwDjQUOEBY)

---

### Post by iforgetagain on 2014-06-28
OK. Now it makes more sense that I could not figure it out. Thank You Lisati.
The next step for me then is to ask; Can I check the download's md5sum and that other check of sh something from my Vista based system?

EDIT saw the new posts after posting. Thanks all I will check the links.

Well I am even more lost.
What is the 1st thing I need to do, to do the md5sum and sha1 check on the downloaded Ubuntu8 14.04 on my desktop?

Well I am even more lost. I tired to watch that vid but the curser was extremely distracting I couldn't follow him. 

What is the 1st thing I need to do, to do the md5sum and sha1 check on the downloaded Ubuntu8 14.04 on my desktop?

---

### Post by Vladlenin5000 on 2014-06-28
OK, let's get to the bottom of this...
Chances are you don't need it anyway. Do you at least understand what it is for? It's only to check if your downloaded file isn't corrupt and nowadays that rarely happens. Plus, whenever you need to be certain it doesn't you can check it immediately after the download has finished from within many download managers already available for Windows and others. One that immediately comes to mind is the Firefox DownThemAll add-on. With that one you can copy/paste the hash into the proper field and DTA! will check it for you.
Now, you already have the file you want to check, I suppose, therefore there's no point in downloading it again this time with DTA! So... Post#7 again... What exactly you don't understand from the Microsoft support page I linked?

---

### Post by iforgetagain on 2014-06-28
OK I have quick hash open on my desktop. I couldn't get the Acetone iso I downloaded to extract and run. 
Can anyone help me from here? I can't find the page with the MD5SUM numbers or the SHA1 numbers and I am unsure of exactly what to do with them in this interface.

---

### Post by Vladlenin5000 on 2014-06-28
What you do with the results has been explained in post #4. It's the same regardless of what method you use to get them.
Here's the hashes for all different ISOs of the current version: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes) (the hash for "desktop-amd64" is dccff28314d9ae4ed262cfc6f35e5153 and so on...).

I never used the software you now have but I suppose you have to open the downloaded file from within that software and somehow ask it to verify the hash. Then just COMPARE (with your eyes only); if they match you have a good download; you don't if they don't. Keep in mind giving support for Windows software is way beyond the scope of this forum and unfortunately you never answered my previous question about what you don't understand in the official Microsoft support document. The thing is: Windows already has native tool, albeit a command line one (get used to it), to do just that and is so SIMPLE to use. Just open a terminal (CMD in Windows) and type: ```
FCIV -md5 path\filename.ext
``` where *path* is the full path to your downloaded file, something like C:\users\your_user_name\desktop (?? not really sure because I DON'T use Windows)...

---

### Post by iforgetagain on 2014-06-28
> **Vladlenin5000 said:**
> OK, let's get to the bottom of this...
Chances are you don't need it anyway. Do you at least understand what it is for? It's only to check if your downloaded file isn't corrupt and nowadays that rarely happens. Plus, whenever you need to be certain it doesn't you can check it immediately after the download has finished from within many download managers already available for Windows and others. One that immediately comes to mind is the Firefox DownThemAll add-on. With that one you can copy/paste the hash into the proper field and DTA! will check it for you.
Now, you already have the file you want to check, I suppose, therefore there's no point in downloading it again this time with DTA! So... Post#7 again... What exactly you don't understand from the Microsoft support page I linked?

OK no we are caught up to each other I had to go do something. I used the command they had in the cmd window and it did not work otherwise it seems like a lot of talknig about assumed things which are not being mentioned. I don't need a pedant just the facts of what needs doing. Sort of like I don't need to know how yeast works to know I need to put 1 teaspoon in the recipe.  I understand the importance of specificity. 
But to end this the easy way you provided I can get that addon and download it again and use it to check. I forget if the site gave me the numbers for the download when I did it or if it was on another page. The last page I linked to from your first link had a list on clicking the first one gave a series of numbers not distinguished form each other or to what they belonged. 
 here it is. I suspect the number i need is on it but I am unsure of how to distinguish it. 
dccff28314d9ae4ed262cfc6f35e5153 *ubuntu-14.04-desktop-amd64.iso
c4d4d037d7d0a05e8f526d18aa25fb5e *ubuntu-14.04-desktop-i386.iso
01545fa976c8367b4f0d59169ac4866c *ubuntu-14.04-server-amd64.iso
08d25bf879e353686a974b7b14ae7d81 *ubuntu-14.04-server-i386.iso
b31731ea6cdbebe1d02f8193db420886 *wubi.exe

And Thank You for the help.

---

### Post by iforgetagain on 2014-06-28
I got DTA and am downloading Ubuntu 14.04 anew. I deleted the last version.  
l found the page for Ubuntu Hashes [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
I will repost when it is completed and I try to use the dTa.

---

### Post by iforgetagain on 2014-06-28
Ok it finished downloading and dta did nothing. Right clicks do not offer anything new. I checked addons and I could detect no part of the options that would let me do an MD5sum or SHA1 check.

---

### Post by Vladlenin5000 on 2014-06-28
Assuming you're downloading a plain desktop version for a common PC (ie, not the server or Mac versions or whatever else is there) then the onlçy thing you need to be sure is whether you're downloading the 32-bit or the 64-bit version. That is one of this two: ```
[TABLE]
[TR]
[TD] dccff28314d9ae4ed262cfc6f35e5153 [/TD]
[TD] ubuntu-14.04-desktop-amd64.iso [/TD]
[/TR]
[TR]
[TD] c4d4d037d7d0a05e8f526d18aa25fb5e [/TD]
[TD] ubuntu-14.04-desktop-i386.iso [/TD]
[/TR]
[/TABLE]

```

**Obs.: In DTA! you need to have the hash before starting the download -and- paste it without any additional space at the beginning or the end in the proper field (last one of the dialog window) -and- make sure you select the correct checksum type which is MD5 in this case.**

---

### Post by kansasnoob on 2014-06-29
Why not just use winMD5Sum as described here:

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows)

---

### Post by iforgetagain on 2014-06-29
EDIT: I am trying kansasnoob idea. I never scrolled down the page that far! I would never have thought to find that there. Seems like it should be at the very top.


I have burned the ISO to a disk and it went well. I would still like to be able to check the download I made it from.

I really appreciate the help offered but something intrinsic is missing from it. Somehow the explanations seem to me to be starting @ 2,3,4 > steps into a process. You are all doing something or things you have internalised so well it is unconscious, that you are not telling me and that is why I cannot comprehend your responses. 
For instance in this statement;
**"Obs.: In DTA! you need to have the hash before starting the download -"** OK but then what? **"paste it without any additional space at the beginning or the end in the proper field"  **What field? When did something with a field come into the process? "** make sure you select the correct checksum type which is MD5 in this case." **Obvious enough but again when did anything from which or in which I can do things come into the equation? 

You see? You know more than you realise and because it is so much you have taken to using a kind of shorthand which is ok with fellow speakers but when you speak to a newbie like me I am lost...:)

---

### Post by iforgetagain on 2014-06-29
SUCCESS! Thank You all.
kansasnoob idea of using the instructions at the bottom of the Ubuntu md5sum page "MD5SUM On Windows" worked. 
Seems like that info should be at the top or linked at the top of that page.

---

### Post by Vladlenin5000 on 2014-06-29
As I said before you should be fine with the one you got and already burned but since you asked for clarification here it goes (please don't pay attention to the language and instead focus on the dialog boxes/windows which should be exactly the same for any language and for any Firefox version running in any OS it supports, ie, it looks exactly like this regardless of the OS).

1. Whenever you click in a download link in Firefox with DTA! this is what happens:
[IMG]http://i60.tinypic.com/2jbwmrs.png[/IMG]

The select option is the one you need to use the method I described earlier. Always the full "DownThemAll!". dTa OneClick! automatically starts the download to the last used location without further questions. It's useful only we need to download several files to the same location -and- we don't need to care about checksum or changing any of the advanced options. For the case in discussion ALWAYS the "DownThemAll!" option.
Click OK.
The following dialog should then appear:
[IMG]http://i59.tinypic.com/28i86d0.png[/IMG]

And as you can see the last field is conveniently called "Checksum (Hash)".
Paste the hash here (I won't say obviously again but yes, it should be obvious). Remember to copy the hash only, no spaces at the beginning or at the end. It won't work otherwise.
Immediately after pasting the hash the dropdown menu at the left (in the image showing SHA1) becomes active and then you should select the checksum type which is this case is MD5.
Then - and only then - you can click start.

You download will proceed as normally but it'll be checked against the provided hash as soon as it is finished.

---

### Post by coffeecat on 2014-06-29
> **iforgetagain said:**
> or linked at the top of that page.

Which it is:

> Contents

...
...

6. MD5SUM on Windows

---

### Post by iforgetagain on 2014-06-29
Thanks coffeecat, I missed that. I guess I was assuming something I did not realise. 

Vladennin5000, I appreciate the effort but when I download in FF that DTA window does not open. I just tried to download Ubuntu again to prove it to myself. It just normally downloaded. 
Does this sentence "1. Whenever you click in a download link in Firefox with DTA! this is what happens." have a secondary meaning than what is apparent to me? I see it saying that DTA will open on its own if I am in FF when I click download. Maybe it implies I have DTA open (which also means FF is open) and am somehow using DTA to download the program? If not the second meaning then I may have a FF/DTA corruption issue which is not part of this sites perview.

---

### Post by Vladlenin5000 on 2014-06-29
> **iforgetagain said:**
> Vladennin5000, I appreciate the effort but when I download in FF that DTA window does not open.

I goes without saying that everything I discussed before IMPLIES you can't have the default automatic download to the Downloads folder in Firefox. Without changing it to "always ask..." (preferences > general tab) Firefox will always download to that folder using it's internal standard download tool and not any add-on. In this scenario no dialog window is shown, it just downloads to the default folder without further questions.
If you already changed it and the dialog appears without the DTA! additional options then of course something is wrong. Either DTA! isn't installed, you didn't restart Firefox after installing the extra or something else I can't figure out right now but definitely something IS wrong, very wrong...

---

### Post by iforgetagain on 2014-06-29
The Options\general tab\downloads  was set to desktop not always ask. 
I think we disagree on the "it goes withjout saying" part, since it is a critical part of using the program you suggested, the instruction to change the setting was necessary for me. 

Thank you, I think it will be fine now.

---

### Post by Vladlenin5000 on 2014-06-29
Sorry, most people I know that use Firefox - regardless of their OS preference - change that setting immediately. That's why I forgot to mention it. Sorry also for assuming it should be easy to figure it out anyway.

---

