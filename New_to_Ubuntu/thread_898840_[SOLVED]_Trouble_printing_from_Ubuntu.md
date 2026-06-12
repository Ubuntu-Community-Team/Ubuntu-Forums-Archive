---
title: "[SOLVED] Trouble printing from Ubuntu"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by onecuwldood on 2008-08-23
I'm totally new to Ubuntu. I have a Lexmark Optra T612 on my network using the network connection on the printer. I don't have any problem printing to it from Windows machines.



I've installed Ubuntu 8.04 and didn't have any trouble installing the printer in Ubuntu, but when I try to print to it (even the test page) it only prints line after line of text. I will give a few lines of what it prints below when printing the test page. Please, any help anyone can offer.  Thank you.


%!PS

    %%  %%

          <</ManualFeed false>>setpagedevice

                                            <<Duplex false>> setpagedevice

                                                                          %!PS-Ad
obe-3.0

       %%Title:PPR Test Page	
		            %% DocumentNeededResources:font Helvetica
                                                                     %%For; (da
vid)
    %RBINumCopies: 1
                    %%Pages: (atend)
                                    %%BoundingBox: (atend)
                                                          %%Endcomments
                                                                       %%BeginPr

---

### Post by onecuwldood on 2008-08-23
Well, the post didn't turn out like it prints it on the sheets, the post took out all spaces. But it prints several sheets of this when printing even the test page. I've been cancelling the print job from the printer's control panel before it goes through a whole tray of paper.

Thanks again to any help.

---

### Post by phidia on 2008-08-23
Check [this page]("http://openprinting.org/show_printer.cgi?recnum=Lexmark-Optra_T612") on your printer for some set up help.

---

### Post by onecuwldood on 2008-08-23
Thank you so much for the link. It was a simple fix. I needed to set the printer to PS emulation.

---

