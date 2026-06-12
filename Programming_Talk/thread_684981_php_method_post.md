---
title: "php method post"
date: 2008-02-01
forum: Programming Talk
---

### Post by carteris21 on 2008-02-01
Hello,
   i got a problem with method post, i got a simple example:

<?php $name = "John"; $age = 18;?>
<form action="welcome.php" method="post">
Enter your name: <input type="text" name="name" value="<?php echo $name;>"/>
Enter your age: <input type="text" name="age" value="<?php echo $age;>" />
<input type="submit" />
</form>

It seem's ok, but some browsers save information identified by names, if sometime you edit 'name' and 'age' inputs for example Luck 22. Later then you just open page can get inputs values not John 18, but Luck 22. How to avoid this situation? If remove attribute "name", would be ok, but how to get submited information. Maybe there some methods to get inputs information by id...

Thanks.

---

### Post by LaRoza on 2008-02-01
Use the ID attribute and the NAME attribute, and make them the same value.

(Except for checkboxes, where the ID's have to be all different)

---

### Post by carteris21 on 2008-02-01
i have found simple solution insert autocomplete="off" in form tag.

---

### Post by mech7 on 2008-02-01
> **carteris21 said:**
> i have found simple solution insert autocomplete="off" in form tag.

It's not valid but it does work :p

---

