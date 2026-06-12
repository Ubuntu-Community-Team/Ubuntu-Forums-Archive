---
title: "Getting the Signature Key using GPG commands"
date: 2018-03-05
forum: New to Ubuntu
---

### Post by nathan137 on 2018-03-05
Step Three of the Verify your Ubuntu 16.04.4 Download tutorial titled "Get the Signature Key."  I have verified that GnuPG 2.2.4 is installed and responding to the --version command.  The instruction is to type this comand line next:

[COLOR=#333333][FONT=&amp]gpg [/FONT][/COLOR][COLOR=#333333][FONT=&amp]--[/FONT][/COLOR][COLOR=#333333][FONT=&amp]keyserver hkp[/FONT][/COLOR][COLOR=#333333][FONT=&amp]:[/FONT][/COLOR][COLOR=#333333][FONT=&amp][I]//keyserver.ubuntu.com --recv-keys "8439 38DF 228D 22F7 B374 2BC0 D94A A3F0 EFE2 1092" "C598 6B4F 1257 FFA8 6632 CBA7 4618 1433 FBB7 5451"

[/I][/FONT][/COLOR]But when I do nothing happens, the cursor just blinks.  So I took out the spaces between the 4 digit strings like so
[COLOR=#333333][FONT=&amp]gpg [/FONT][/COLOR][COLOR=#333333][FONT=&amp]--[/FONT][/COLOR][COLOR=#333333][FONT=&amp]keyserver hkp[/FONT][/COLOR][COLOR=#333333][FONT=&amp]:[/FONT][/COLOR][COLOR=#333333][FONT=&amp]*//keyserver.ubuntu.com --recv-keys "843938DF228D22F7B3742BC0D94AA3F0EFE21092" "C5986B4F1257FFA86632CBA746181433FBB75451"*[/FONT][/COLOR]

And then it worked but the pub date line is different
The tutorial says: [COLOR=#333333][FONT=&amp]1024D[/FONT][/COLOR][COLOR=#333333][FONT=&amp]/[/FONT][/COLOR][COLOR=#333333][FONT=&amp]FBB75451 [/FONT][/COLOR][COLOR=#333333][FONT=&amp]2004[/FONT][/COLOR][COLOR=#333333][FONT=&amp]-[/FONT][/COLOR][COLOR=#333333][FONT=&amp]12[/FONT][/COLOR][COLOR=#333333][FONT=&amp]-[/FONT][/COLOR][COLOR=#333333][FONT=&amp]30
[/FONT][/COLOR]my screen say dsa1024 2004-12-30

Should I be worried?

---

