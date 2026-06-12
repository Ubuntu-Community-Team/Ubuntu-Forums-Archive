---
title: "Firefox"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-04-14
When we click on the PRINT PREVIEW button in firefox we come across a set of default setings e.g. filename, location, url, page number, date etc.
In my case i need to change all of them every time i take a print / save as pdf. 
In the attachments here :

F-0 is shows the default values
F-1 is what i wish to have e.g. all blank and 
F-2 should have the title of the page as the file name and Desktop as the location.

I read a few times abt some 'config' comand.
I tried it once but found too many settings there and was confused :)
Can any one give some advise.

---

### Post by lovinglinux on 2012-04-14
Type about:config in the address bar, then search for these settings below, right click on each of them and select "Reset":

[I]printer_PostScript/default.print_headerleft
printer_PostScript/default.print_headerright
printer_PostScript/default.print_footerleft
printer_PostScript/default.print_footerright[/I]


Search for *printer_PostScript/default.print_to_filename*, right-click, select "Modify", change the value to ~/Desktop/mozilla.pdf

That will change the path to Desktop, but the title I couldn't make it dynamic.

---

### Post by 3dmatrix on 2012-04-15
> **lovinglinux said:**
> Type about:config in the address bar, then search for these settings below, right click on each of them and select "Reset":

[I]printer_PostScript/default.print_headerleft
printer_PostScript/default.print_headerright
printer_PostScript/default.print_footerleft
printer_PostScript/default.print_footerright[/I]


Search for *printer_PostScript/default.print_to_filename*, right-click, select "Modify", change the value to ~/Desktop/mozilla.pdf

That will change the path to Desktop, but the title I couldn't make it dynamic.

Thanx ! I tried what you told me to do for the header and footer. I feel it should not be RESET but modified. Because when i reset them it gets removed from the about:config list and i found no changes in the browser. So i had to add it again as a NEW STRING with a BLANK VALUE. That solved the header and footer problem. I tried using &T and $T for dynamic naming of the generated pdf as the Title of the webpage but it didnt work. Does any one has any recomendation ?

I also face another problem in Firefox where the spell check does not works automatically at times but sometimes it does. What is going wrong ?

---

