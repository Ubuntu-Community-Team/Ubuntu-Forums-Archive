---
title: "Closing Javascript table?"
date: 2009-08-13
forum: Programming Talk
---

### Post by ArmenianLeader4 on 2009-08-13
Is there any way to make a table close using javascript or HTML? I can't use CSS ATM, because of specific complications i won't get into right now, but I want to somehow generate a box that can be closed, similar to the one on the home page of_ _[http://4chan.org]("http://4chan.org/")
Any help would be appreciated, and I don't want to use the <div> system that is currently implied on 4chan, so, any javascript would help.

---

### Post by Mirge on 2009-08-13
[jQuery]("http://www.jquery.com/")

---

### Post by ArmenianLeader4 on 2009-08-13
Not exactly what i wanted, but Ill give them another shot. also, BUMP.

---

### Post by Mirge on 2009-08-13
> **ArmenianLeader4 said:**
> Not exactly what i wanted, but Ill give them another shot. also, BUMP.

jQuery is a JS library. Using jQuery, you can hide a table very easily. IE:

```

<script type="text/javascript" src="jquery.pack.js"></script>
<script type="text/javascript">
function hideTable()
{
$('#simpleExample').hide();
}
</script>
..
..
..
<a href="javascript:hideTable()">Hide Table</a><br/>

<table id="simpleExample">
<tr>
<td>Hi there.</td>
</tr>
</table>

```The above is just a quick & dirty example.

For doing the above, you wouldn't need jQuery at all... you can set the element's "display" style to "none" to achieve the same effect. However, jQuery makes many, many other things considerably easier.

If you really mean you can't use CSS _at all_, I can't really fathom why... but in that case you'd need to remove the element from the HTML code altogether, both of which you can do with jQuery & without... but again I recommend jQuery.

---

