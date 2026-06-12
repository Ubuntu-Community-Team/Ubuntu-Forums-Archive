---
title: "Why is my PHP $_POST array empty on submitting a form to a script?"
date: 2016-04-01
forum: Programming Talk
---

### Post by Steve_Corenflos on 2016-04-01
I'm trying to write a simple web app, but when I try to update my page the PHP script is returning an empty array for $_POST. This same script works on other installations of Ubuntu/Apache, but for some reason not on my Ubuntu 15.10/Apache 2.4.12 -- even though I've made no configuration changes to Apache or PHP and installed them through apt-get. I've been going crazy trying to figure this out! Thanks for any help!


```

<form action="<?php echo $_SERVER['PHP_SELF']; ?>" method="post" enctype="application/x-www-form-urlencoded">
    <label for="letter">Guess a letter:</label>
    <input type="text" name="letter" id="letter" size="2" maxlength="1" />
    <input type="submit" name="guess" value="Guess" />
</form>

```

---

### Post by SeijiSensei on 2016-04-01
I don't see why either, Steve.  Have you tried looking in $_REQUEST to see if the field value shows up there?

I don't use "/>" to close form fields, just ">".  I don't know if that matters at all.

---

