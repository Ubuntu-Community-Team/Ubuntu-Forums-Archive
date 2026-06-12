---
title: "Wine: Various Errors when installing .NET 4.8"
date: 2023-08-02
forum: New to Ubuntu
---

### Post by interval0043 on 2023-08-02
I was attempting to install Visual Studio, so I had to install .NET 4.6 or higher first. Simple enough, it seemed. I have received 4 errors as of now, one resolved on my own. The other 3 I'm confused about:

1: ```
'wine: could not open working directory L"C:\\windows\\sysnative", starting in the Windows directory'.
``` I know this happens because the folder doesn't exist in my case, since I went to it, and it wasn't there. *The question is, why?* Not to mention, I added the folder, but all it did was get rid of the message. Supposedly, it fixed that one.

2: ```
'0120:err:mscoree:LoadLibraryShim error reading registry key for installroot'
```
I can gauge that it has to do with wine's system, and mscoree feels like a dll, or something important. But, as of a count, it happens 16 times in a row.

3: ```
'0108:error:ole:CoUnititialize Mismatched CoUnitialize'
```
This happens whenever I click 'Restart' when the setup finishes. Because yes, it does say it finishes, but these errors tell me it might not have done it fully. Especially because after this, Visual Studio *still* doesn't install.

I am trying to do this because I am more used to Visual Studio than VS Code, by a wide margin.

Edit: As of trying it again, error 2's '0120' became '011c', and error 3's '0108' became '0104'. What do these even mean?

---

### Post by interval0043 on 2023-08-02
Fix to error 3: The emoji :o is supposed to be a colon and an 'o'.

---

### Post by QIII on 2023-08-02
Those emojis are created by plain text.  As a rule, please include all issued commands and results returned within code tags.  This will preserve formatting and make your posts easier to read and understand.
To use code tags:

1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by QIII on 2023-08-02
According to Wine's Application Database, [Visual Studio is rated as "garbage" for about the last 15 years.]("https://appdb.winehq.org/objectManager.php?iId=892&sClass=application")

VS Code works, but it is really nothing more than a text editor and has none of the higher-level capabilities of a real IDE.

I am a Linux guy at heart, but for almost 25 years I made my small fortune with my software development company writing bespoke solutions for Windows.  I have had both physical and virtual machines running Windows so that I could use VS.  I'm semi-retired now, having maintained only one client, but I still have a Win 10 VM to work on things for them.

That is all to say, if you are doing Microsoft stuff, use Microsoft stuff -- and Windows if the tools work better.

---

### Post by interval0043 on 2023-08-02
Thanks for the info, I might as well dualboot since windows on this thing is much slower than Ubuntu. I probably should install .NET 4.8 anyway, since for some reason in VS Code it just isn't letting me debug. That's something I'll take up with Microsoft Community.

---

