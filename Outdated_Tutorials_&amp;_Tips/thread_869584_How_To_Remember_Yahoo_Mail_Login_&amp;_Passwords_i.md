---
title: "How To: Remember Yahoo Mail Login &amp; Passwords in Firefox"
date: 2008-07-24
forum: Outdated Tutorials &amp; Tips
---

### Post by ramjet_1953 on 2008-07-24
[SIZE="5"][CENTER]How To Remember Yahoo Mail Logins & Passwords in Firefox[/CENTER][/SIZE]

An issue that many people may have with Firefox is that even with the [COLOR="Blue"]Secure Login add-on[/COLOR], Firefox doesn't recognise the Yahoo Mail login screen.

Back in August of 2006, kerry_s gave me a tip that has been very useful. As as I have just installed Hardy onto a spare HDD and am deciding whether to switch to it from Gutsy, I needed to implement saved passwords for Yahoo Mail again.

The process is quite simple. All you need to do is to create a [COLOR="Blue"]bookmarklet[/COLOR], with some Java script.

1. Make sure that the [COLOR="Blue"]Bookmarks Toolbar[/COLOR] is visible. This is achieved by clicking on [COLOR="Blue"]View>Toolbars[/COLOR] and selecting [COLOR="Blue"]Bookmarks Toolbar[/COLOR].

2. Next add the [COLOR="Blue"]Secure Login Add-On[/COLOR]. Navigate to [COLOR="Blue"]Tools>Add-ons[/COLOR] and navigate to the Firefox website and search for it and install it. Firefox will need to re-start, before the add-on becomes active.

3. Right-click on a vacant space on the Bookmarks Toolbar. When the window opens, enter [COLOR="Red"]Remember Password[/COLOR] into the [COLOR="Blue"]Name Field.[/COLOR]

4 Next, copy and paste this code into the [COLOR="Blue"]Location Field[/COLOR]

```
javascript:(function(){var ca,cea,cs,df,dfe,i,j,x,y;function n(i,what){return i+%22 %22+what+((i==1)?%22%22:%22s%22)}ca=cea=cs=0;df=document.forms;for(i=0;i<df.length;++i){x=df[i];dfe=x.elements;if(x.onsubmit){x.onsubmit=%22%22;++cs;}if(x.attributes[%22autocomplete%22]){x.attributes[%22autocomplete%22].value=%22on%22;++ca;}for(j=0;j<dfe.length;++j){y=dfe[j];if(y.attributes[%22autocomplete%22]){y.attributes[%22autocomplete%22].value=%22on%22;++cea;}}}alert(%22Removed autocomplete=off from %22+n(ca,%22form%22)+%22 and from %22+n(cea,%22form element%22)+%22, and removed onsubmit from %22+n(cs,%22form%22)+%22. After you type your password and submit the form, the browser will offer to remember your password.%22)})();
```

5. Click on the [COLOR="Blue"]Save button[/COLOR].

That's it!

The next time you want to save a Yahoo email password into the wand, just click on this bookmarklet before you send your username and password.

Next time, you can just use Secure Login's wand to open your account.

Thanks again, to kerry_s for this great little bit of code.

Regards,
Roger :cool:

---

