---
title: "Javascript dropdown text"
date: 2009-11-05
forum: Programming Talk
---

### Post by easybake on 2009-11-05
Ok, first off I would like to say that my javascript knowledge is minimal at best but I am trying to learn. Here is my problem:

I am running a dropdown menu with options like this
```
<select name="menu" style="font-family:'Arial';color:#0066CC;background-color:#FFFFFF;font-size:10pt;">
<option value="">Choose One-</option>
<option value="Guarantee.tpl">Our Guarantee</option>
<option value="green.tpl">Green</option>
<option value="Packaging.tpl>Packaging</option>
<option value="card.tpl">Gift Cards</option>
</select>
<input type="button" onClick???????? value="GO!">
</form>
```

What I want to do is have the template files load below where the dropdown menu is. This way, I can have a single page that contains only the content selected by the drop down menu.

The problem I am having is the things I have found only have the content load in a new page/tab. Any ideas on how I could do this.

The .tpl files are html templates which are used with ```
{include file="template.tpl"}
```

---

### Post by korvirlol on 2009-11-05
if you are using a scripting language like php, you can do something like;

[PHP]$selectoptions = file_get_contents(/path/to/your/tpl/file.tpl);
[/PHP]
and in the html:

[PHP]<select>
     <option></option>
     <?php print $selectoptions; ?>
</select>[/PHP]

---

