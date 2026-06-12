---
title: "PHP Forms"
date: 2008-07-04
forum: Programming Talk
---

### Post by Tux.Ice on 2008-07-04
ok im creating a php form, LIke This

<FORM 1 action=MAILTO:BLA@BLA.BLA>
TEXT BOX HERE
CHECK BOX HERE
<SUBMIT>
</FORM 1>
<FORM 2 action=Cpemail.php>
TEXT BOX
TEXT BOX
PSSWRD BOX
JS PSWRD METER
<SUBMIT>
</FORM 2>

i was thinking of creating another php file called action.php, and in there having it seperatly handle each input, FOR EXAMPLE

<FORM 1 action=action.php
TEXT BOX 1 HERE
CHECK BOX 1 HERE
TEXT BOX 2
TEXT BOX 3
PSSWRD BOX 1
JS PSWRD METER 1
<SUBMIT>
</form 1>

AND THEN IN action.php

TEXT BOX 1 && Check BOX 1 == mailto:
PSSWRD BOX 1 && JS PSWRD METER 1 == cpemail.php 

the cpemail.php is a script used to create an e-mail account through cpanel.

Oh, BTW i know the above diagrams arent actual PHP, JavaScript, HTMl or any other code.

---

### Post by henchman on 2008-07-04
Sorry, but i don't get you question :>

but instead of doing ```

<FORM 1 action=MAILTO:BLA@BLA.BLA>
```

better send it to an php script which sends the mail via mail() or anything else... otherwise the user will have to use his/her own local installed mail program and some users don't have such a program, because they use webmail clients...

if you would like to know which of your form solutions is the "better" one, you may give us the real names / labels for the form elements...

---

### Post by LaRoza on 2008-07-04
Ok, before we even look at the code, use [noparse][html][/html] tags, [php][/php] tags or ```

``` tags.[/noparse]

And make sure the markup is valid, your code is so invalid it is meaningless.

---

### Post by mssever on 2008-07-04
You made a statement, rather than asking a question. However, I'll make a couple of statements. :)

First, in addition to the other concerns raised, using mailto to send a form is a bad idea because it exposes that address to spammers. I make it a policy to never put a machine-parsible email address in any publicly accessible Internet location for any reason. The only exception is for Project Honeypot and similar.

Secondly, while I think I understand your form pseudocode (though why not just use real code?), your PHP pseudocode is meaningless.

---

