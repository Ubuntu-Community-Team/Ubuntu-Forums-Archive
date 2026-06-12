---
title: "Switching parents to ubuntu"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by cha0s_unity on 2008-06-27
Hey guys. My parent's keep having trouble with XP and i'm trying to get them to change over to Ubuntu. My parents are not very computer minded people and only use the computer for basically using internet, email, pictures, and the like. I can't think of anything that a fresh install of 8.04 doesn't have they would need. However I am still fairly new to Ubuntu and feel I should ask to see if anyone recommends adding anything that my parents may need. So if anyone knows anything I should put on their machine let me know

Could someone also clear up for me the difference in add/remove applications and synaptic packet manager? Here's how I understand it. Add/remove has the most used programs from the Ubuntu repository, and synaptic has all programs from ubuntu and other compatible repositories. Is this right?

-- Thanks for your help

---

### Post by tamoneya on 2008-06-27
here is how I think of package manager and add/remove:

add/remove = programs and things that go in the menus on gnome panel

package manager = everything in add/remove + libraries + everything else needed to run the OS (kernel headers are in there)

To ease the transition it may help to change the theme on them just so that it actually looks like windows.  I know it may seem like a small thing to someone like you or me but to some one who doesnt know computers well if things arent where they always were they get very confused very quickly.  Many people like your parents may have trouble if the windows start button suddenly moved to the lower right instead of lower left.  Someone like you or me wouldnt think twice about the UI change.

---

### Post by zeller on 2008-06-27
Only thing I can think of is actually a question.

Do they use a Windows program to do Taxes? If so, there isn't an equivalent in Linux that is supported by the tax software companies out there. Not, yet anyway. They can do them online through the web browser for a select few companies though.

Do you know how to change the look of the DE to look like Windows? If you're fearful they may reject it based on appearance then you may want to check out here on the forums just how to do that. If that's not an issue, great!

Good luck with converting them! I've all but converted my wife with exception to the tax issue. Otherwise, she doesn't mind it at all. Basic internet surfing, email, music, pictures - all easy for Ubuntu to handle, so no problems there.

---

### Post by kansasnoob on 2008-06-27
As a matter of personal preference I'd say start with a dual boot. That way if they just hate Ubuntu it can be removed and they can go back to Windows.

I started using a dual boot for two reasons: my scanner wouldn't work properly in Ubuntu and I have a bunch of photo Cd's that are is .psf format (photo studio format?) that I couldn't get Ubuntu to read.

I've since replaced that scanner (I was overdue for a new printer anyway, so I got a new all-in-one HP), and have Irfanview installed thru Wine, but I still have XP just in case ................ although I haven't used it in some time, but I still boot it once a week just to keep AV up to date.

Just for fun, a screen shot of my "modified" Ubuntu desktop:

[ATTACH]75483[/ATTACH]

Notice I've changed to only a lower panel and have only the applets I want in that panel. Sort of a bit more window-ish.

When I've set up Ubuntu desktops for other seniors I tend to "hide" all of the stuff they'll never use just by going to System > Preferences > Main Menu. They call me whenever something breaks anyway:)

---

### Post by kansasnoob on 2008-06-27
"Do they use a Windows program to do Taxes? If so, there isn't an equivalent in Linux that is supported by the tax software companies out there. Not, yet anyway."

Excellent point Zeller!

---

### Post by sailor2001 on 2008-06-27
I found it easier to convert a senior to linux using elyssa mint...that looks most like windows and seems to be the easiest for them to understand.

---

### Post by blairm on 2008-06-27
Hi,

Switched my parents (in early 60 and 70s) to ubuntu a while ago for the same reason, and it's proved very successful. A couple of pieces of advice:

1) Dual boot, so they have the option of reverting to windows if they need to. Aside from anything else, they found it much easier to learn ubuntu knowing they had a safety net if things weren't going well.

2) Make sure their hardware is supported!

3) I changed my parents over while I was staying with them for a week (they live in another city) and if possible I recommend you do the same; so much easier to solve any problems and teach the basics in person.
 
4) Talk to them first about what their needs are eg they may have used the computer to edit photos, but what did they do to them? No point in overwhelming them with something like gimp if all they did was crop the pics.

5) Re the UI: everyone's different, and you know your parents far better than we do! I started mine on the basic gnome desktop which they liked because it was uncluttered, but YMMV.
 

Both parents have embraced Ubuntu to such a degree they have booted into windows only five times in the past year - and that was to get updates etc.

Blair

---

### Post by RATM_Owns on 2008-06-27
I guess for the most "Windows feel" Ubuntu can provide, install the Mint Menu
(I think this repository works:
deb [http://www.linuxmint.com/repository](http://www.linuxmint.com/repository) romeo/)
and move the Mint Menu icon to the bottom right, to the left of the "Show Desktop" icon. You can remove or just move anything by right clicking and choosing move or remove from panel.

You can also find a Windows theme for Gnome.

---

### Post by abn91c on 2008-06-27
Just use Kubuntu instead, since the menus are similar to windows XP, just remame the konqueror shortcut to web browser or something like that, same for kmail, just rename icon to email just to make it easier for them

---

### Post by tubbygweilo on 2008-06-27
Another idea will be to ensure that you have taken all steps to make the playing of music and the viewing of films via cd and dvd idiot proof by ensuring that you have everything from the [restricted formats]("https://help.ubuntu.com/community/RestrictedFormats#head-6524aff77dac67a074cbaf46657ce6c2104341e2") documents loaded and working. If they have been used to slipping in a silver disk and having it work under windows then the same should happen under Ubuntu otherwise they might question the move away from windows. 

I also placed the most used icons like FireFox, ThunderBird and GoogleEarth on the Gnome launcher panel at the top of the page so they can run something with just one click rather than navigating with shaky hands through the Application > menu while searching for the right application. 

Would you consider giving them sudo access so as to perform their own updates or would you think about doing it remotely from your desktop? 

I have done all this except for the system update stuff for an uncle of mine who lives just over an hour away and any system updates or tweaking that needs to be done I do this for him during my weekly visits.

---

### Post by timcredible on 2008-06-27
> **zeller said:**
>  If so, there isn't an equivalent in Linux that is supported by the tax software companies out there. .

sure there is - taxact.com.  works perfectly.

as for putting non-technical windows users on ubuntu, i would recommend you remove the bottom panel, move the top panel down to the bottom, add the 'window list' to that panel, add any app they use as a launcher on that panel, then it looks very similar to windows and they don't have to even look for stuff in the menu.  i do that and it goes pretty smooth, i just have the gripes about "the icon looks different" and stuff like that.

---

### Post by Canis familiaris on 2008-06-27
YOu do not need to change the look of Ubuntu. It is uncluttured and easy to use. Just have few sessions with your parents and show them the GUI, its working, and most importantly tell them Linux is not Windows and tell them why the install cd of a popular program given by a friend will not work. Also preconfigure all the hardware and install the ubuntu-restricted-extras and VLC Media player so that they could easily watch movies, go to java and flash sites. 
Also add the desktop icons like Computer, Trash.., yourself
(Steps:
Alt + F2
type gconf-editor
gcpmf-editor
Apps->Nautilus->Desktop)

If you think they require some kind of Windows software, configure WINE or try to set up [this]("http://amitech.50webs.com/ultimate.html")

---

### Post by cha0s_unity on 2008-06-29
Thanks for the help guys. I'm sure it won't be the last time I have something to ask.

---

