---
title: "html + javascript + php query...."
date: 2009-11-13
forum: Programming Talk
---

### Post by maclenin on 2009-11-13
Essentially, I would like to be able to modify the action variable in this statement, dynamically...

```
<form action="target.php" method="post">
```

...to be able to post to, for example, target.php or target_001.php or target_002.php, depending on the nature of the data needing to be posted.

I have set up a form to collect data - and have been able to designate different "targets" as vars - selecting the appropriate "target" based on the data collected, but I can't figure out how to incorporate the selected "target.php", dynamically, into the html...

i.e. <form action="target_001" or "target_002" or ...

...upon submit!

Thanks for any guidance!

---

### Post by sheep1 on 2009-11-13
You may be able to just place different functions (or switch.. ) in the PHP and call the differents function based on the data.  

This may be a solution that would work...

---

### Post by defleopard98 on 2009-11-13
If you need to do it in the page with javascript it's:
```
document.FORMNAME.action="URL"
```or if you want to use jQuery:
```
$('#FORMID').attr('action','URL')
```Of course, replace FORMNAME with the name or FORMID with the ID. And URL with the url of the form(target_001.php,target_002.php...)

---

### Post by maclenin on 2009-11-14
**Rock of Ages!**

Thanks folks, ended up using javascript (as it's what I think I know best)...

```
document.getElementById("elementid").action="url";
```

...thanks again!

---

