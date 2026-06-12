---
title: "firefox 3 showing different in Win and Lin"
date: 2008-06-23
forum: Programming Talk
---

### Post by soapytheclown on 2008-06-23
Hi all, 
   ive got a very weird problem with firefox 3 and its been occuring RC1 it was fine on Beta 5 and presumed it was a bug that would be fixed at on release.

the easiest way to show the problem im getting is by looking at these screen shots, one is ubuntu ff3 final the other is vista ff3 final. notice that the text bars are different lengths, vista is showing them correctly and firefox 2 displays them like that too but ff3 on ubuntu is stretching them, ive tested it on 3 ubuntu machines so its not some weird thing related to my machine.

and just incase ive removed all css and tried it aswell.. same issue
the code behind it is nothing special bog standard html:

[PHP]
<div>Username:
						
<input id="username" type="text" name="username" tabindex="1" size="20" maxlength="20"/>

</div>

<div>Password:					
<input id="password" type="password" name="password" tabindex="2" size="20" maxlength="20"/>
</div>
[/PHP]

can anyone explain why firefox 3 in linux renders it differently :S

thanks in advance :)

---

### Post by samjh on 2008-06-23
The fonts are displayed differently.

On the Linux version of FF3, the fonts are rendered wider than on the Windows version.  So that's probably why the text fields are rendered wider as well.

---

### Post by henchman on 2008-06-23
shouldn't the text above the textboxes be wider then, too?

---

### Post by soapytheclown on 2008-06-23
thanks for the replies, i was about to say what henchamn said, the text elsewhere is fine and i even installed firefox 2 on the same ubuntu machine to see if that was affected, but it rendered correctly, has anyone esle got any ideas?

---

### Post by samjh on 2008-06-23
> **henchman said:**
> shouldn't the text above the textboxes be wider then, too?Not necessarily.

Handling of font width varies a lot between platforms - or more accurately, between font renderers.

This is just a rough guess.  I'm not an font expert, and my HTML knowledge is rudimentary.

[quote=soapytheclown]thanks for the replies, i was about to say what henchamn said, the text elsewhere is fine and i even installed firefox 2 on the same ubuntu machine to see if that was affected, but it rendered correctly, has anyone esle got any ideas?[/quote]Keep in mind that FF3 has enhanced integration of native look-and-feel.  This may be why FF2 displayed everything identically on Windows and Linux, but FF3 does not.

I still think that this is an issue with the font renderers used by respective platforms.

---

### Post by soapytheclown on 2008-07-04
has anyone else got any other ideas on how i can fix this?

---

### Post by henchman on 2008-07-04
You could set a fixed width for your textboxes using css... ```
<input type="text" style="width: 100px;"/>
```

---

### Post by mssever on 2008-07-04
> **soapytheclown said:**
> has anyone else got any other ideas on how i can fix this?
Use CSS to set the width, measured in some unit that doesn't depend on differences in font rendering.

---

### Post by soapytheclown on 2008-07-04
i ended up setting a max-width property for all my input elements which whilst doesnt solve the entire problem stops the longer elements adding extra lines (i have a load of other pages where the problem screws the layout) whilst it works its just annoying that now we're having to make extra changes soley for those of us on running ff3 on linux :@

---

### Post by mssever on 2008-07-04
> **soapytheclown said:**
> i ended up setting a max-width property for all my input elements which whilst doesnt solve the entire problem stops the longer elements adding extra lines (i have a load of other pages where the problem screws the layout) whilst it works its just annoying that now we're having to make extra changes soley for those of us on running ff3 on linux :@
That's not strictly a problem. It's perfectly acceptable for different browsers to have different defaults. You should always specify everything through CSS anyway.

---

### Post by soapytheclown on 2008-07-04
well if its rendering one way in lin and another in windows both on FF3 yet the windows way matches all other browsers then surely there is some problem? i could understand if it was a problem between different browsers but the same broswer different os is why i thoght it was a problem

---

### Post by descendency on 2008-07-04
[http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)

---

### Post by mssever on 2008-07-05
> **soapytheclown said:**
> well if its rendering one way in lin and another in windows both on FF3 yet the windows way matches all other browsers then surely there is some problem? i could understand if it was a problem between different browsers but the same broswer different os is why i thoght it was a problem
And there might be a bug somewhere. But AFAIK, the standards don't specify the default width of input boxes. So technically, the browsers are free to choose the default. Which is why you should explicitly specify it if you care about it.

---

### Post by soapytheclown on 2008-07-05
> **mssever said:**
> And there might be a bug somewhere. But AFAIK, the standards don't specify the default width of input boxes. So technically, the browsers are free to choose the default. Which is why you should explicitly specify it if you care about it.


[http://www.w3.org/TR/html401/interact/forms.html#h-17.4](http://www.w3.org/TR/html401/interact/forms.html#h-17.4)

size = cdata [CN]
    This attribute tells the user agent the initial width of the control. The width is given in pixels except when type attribute has the value "text" or "password". In that case, its value refers to the (integer) number of characters.

As far as i can tell from those notes there is a problem, and just to amke sure i typed 20 characters into the input feild and there was about 8 characters extra blank space in the feilds shown in the screenshots

---

