---
title: "Need some help with javascript and collapsing iframes"
date: 2009-03-03
forum: Programming Talk
---

### Post by jakev383 on 2009-03-03
I'm trying to show some iframes on my page, and have them collapsable. This works now. What I'm looking to do is have some of the frames start collapsed, and some start expanded. I'm not a javascript guru, but hopefully someone out there can give me a hint or bump in the right direction. Here's the code I'm testing:
```

<!--  Begin Javascript for expanding menus -->

<script>
function ShowHide(tab) {
      var t = document.getElementById(tab);
      if (t.style.display == '') {
            t.style.display = 'none';
            t.style.visibility = 'hidden';
      }
      else {
            t.style.display = '';
            t.style.visibility = 'visible';
      }
}

function ShowAll() {
      var t = document.getElementById('info');
      for (var i = 0; i < t.rows.length; i++) {
            if (t.rows[i].id != "control") {
                  t.rows[i].style.display = '';
                  t.rows[i].style.visibility = 'visible';
            }
      }
}

function CollapseAll() {
      var t = document.getElementById('info');
      for (var i = 0; i < t.rows.length; i++) {
            if (t.rows[i].id != "control") {
                  t.rows[i].style.display = 'none';
                  t.rows[i].style.visibility = 'hidden';
            }
      }
}
</script>

<!-- End Java script to expand menus -->

</head>
<body>

<!------- Start top of page ---------->
<!------- Menu on left of page to expand/collapse menus ---------->
<a href="javascript:ShowAll()">Expand all menus</a>&nbsp;<br><a href="javascript:CollapseAll()">Collapse all menus</a></br>
<center>
<!------- End menu on left of page to expand/collapse menus ---------->

<table id="info"> <!-- Begin table for java menus -->

<!------- Begin Display Yahoo ---------->
<tr id="control">
<td bgcolor="#007700" width="100%" id="block1" class="sectionOpen" onClick="ShowHide('StableTab')"><center><font color="#FFFFFF">Yahoo</center></td>
</tr>
<tr id="StableTab">
<td width="100%">
<iframe src="http://yahoo.com" name="stableFrame" width="780" height="550">
</iframe>
</td>
</tr>
<!------- End Display Yahoo ---------->


<!------- Begin Display of Google ---------->
<tr id="control">
<td width="100%" id="block2" class="sectionOpen" onClick="ShowHide('GTab')"><center>Google info</center></td>
</tr>
<tr id="GTab">
<td width="100%">
<iframe src="http://google.com" name="gInfoFrame" width="650" height="120">
</iframe>
</td>
</tr>
<!------- End Display of Google ---------->


</table> <!-- End table for java menus -->
</center>


</body>
</html>

```

Any help is appreciated!

---

### Post by s.fox on 2009-03-03
Hi,

Have you considered using a creative style sheet to make the iFrames start collapsed?  You shouldn't require any more addition javascript.

-Hope this gives you some ideas.

---

### Post by jakev383 on 2009-03-03
> **Ash R said:**
> Hi,

Have you considered using a creative style sheet to make the iFrames start collapsed?  You shouldn't require any more addition javascript.

-Hope this gives you some ideas.


I had thought of this (and am using CSS for text/block formatting anyway) but am not sure how to tie this in with Javascript.

---

### Post by s.fox on 2009-03-04
Hi,

You could use the CSS to set the style of the iFrames when your page first loads.  Then you could use your existing javascript (no changes needed) to collapse and uncollapse them.

-Ash R

---

