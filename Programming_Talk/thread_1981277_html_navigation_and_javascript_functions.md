---
title: "html navigation and javascript functions"
date: 2012-05-16
forum: Programming Talk
---

### Post by maclenin on 2012-05-16
I would like to be able to click imageX on one page (**index.html**) and be taken to projectX on a second page (**projects.html**) - and there is javascript involved....

A. As currently configured...

**index.html**
...if I click image1 **<a href="projects.html"></a>** I am taken to **projects.html**
...if I click image2 **<a href="projects.html"></a>** I am taken to **projects.html**
...if I click image3 **<a href="projects.html"></a>** I am taken to **projects.html**

**projects.html**
project1 is displayed if **<body onload="display_project(1);">** or by clicking tab1 **<onclick="display_project(1);">**
project2 is displayed if **<body onload="display_project(2);">** or by clicking tab2 **<onclick="display_project(2);">**
project3 is displayed if **<body onload="display_project(3);">** or by clicking tab3 **<onclick="display_project(3);">**

B. I would like to be able to...

...click on image1 (index.html) and be taken to project1 (projects.html)
...click on image2 (index.html) and be taken to project2 (projects.html)
...click on image3 (index.html) and be taken to project3 (projects.html)

Thanks for any guidance!

---

### Post by bobman321123 on 2012-05-16
You want to use a picture as a link?
isn't that just ```
<a href="#"><img src="path/to/pic"></a>
```?

---

### Post by bobman321123 on 2012-05-16
something tells me my javascript noobishness has caused me to give an irrelevant answer.....

---

### Post by maclenin on 2012-05-17
**bobman321123!**

It's about reaching out - rather than needing to be right....

Thanks for your suggestion - but, yes, I think the issue has to do more with javascript than html - or, differently, the interaction of the two, to give me the desired result.

project1, project2 and project3 are images stored in a javascript array and are displayed (ad hoc) on the projects.html page using calls to a javascript function [ e.g. display_project(X) ], which are buried in the page's <body> and certain <div> tags and triggered by onload or onclick events, respectively.

My ultimate goal is to find a way to trigger the display_project(X) function (call) from index.html, so that when I click on image1 in index.html, project1 is displayed when the projects.html page opens...same for image2 and image3...

It's **"picture as a link"** on steroids - I want to use the imageX link to not only open a new page (projects.html), but also to bring up a related element (projectX) and its associated content / features, which are dynamically added / replaced on projects.html by the display_project(X) function (which resides in a separate projects.js page).

Thanks, again, for your reply!

---

### Post by Dimarchi on 2012-05-18
Need more clarification, but here goes...

I take it that projects.html merely lists the projects in the following fashion (this stuff for clarification purposes):

Project 1 (visible at all times)
Project 2 (visible at all times)
Project 3 (visible at all times)

Then no Javascript required: you are about to enter the magical world of anchors! :)

```

<a href="projects.html#project1">Project 1</a>
<a href="projects.html#project2">Project 2</a>
<a href="projects.html#project3">Project 3</a>

```and in projects.html file you need a corresponding name attribute at the project starting point...let's say it is a heading of the type h2 (could be some other element entirely...this is just for illustrative purposes):

```

<h2 name="project1">Project 1</h2>
...
<h2 name="project2">Project 2</h2>
...
<h2 name="project3">Project 3</h2>
```Basically, that should be it. It could be that name will not work, I haven't tested this. In that case it may require additional id attributes (id="project1" etc.), or instead of name merely id.

A new window still wouldn't need Javascript:
```

<a href="projects.html#project1" target="_blank">Project 1</a>
<a href="projects.html#project2" target="_blank">Project 2</a>
<a href="projects.html#project3" target="_blank">Project 3</a>

```There are other values than _blank available, but that should suffice. A simple search should give you links enough to both attributes I mentioned above: name and target. The use of either or both will not exclude the use of Javascript in the manner you have described, that is, adding content dynamically.

Am I on the correct track here with what you are after?

---

### Post by maclenin on 2012-05-18
**Dimarchi!**

I love magic - though the particular brand you've described (with anchors) is one with which I have not dabbled - merely googled. However, you have presented a wonderfully lucid model to which I shall return, as the need for such spells arise!

Let me "simplify" to clarify (perhaps) what it is I seek (and, perhaps, what I might have **[COLOR="DarkGreen"]found[/COLOR]**):

**images in play:**

image1.jpg
image2.jpg
image3.jpg

project1.jpg
project2.jpg
project3.jpg

**project.js**
```

function **display_project(p)** {document.getElementById("project").src="project"+p+".jpg";}

```

**project.html**
```

<body onload="**display_project(1)**;">

<img id="project" src="">

<div id="tab1" onlcick="**display_project(1)**;">Tab1</div>
<div id="tab2" onclick="**display_project(2)**;">Tab2</div>
<div id="tab3" onclick="**display_project(3)**;">Tab3</div>

```

**index.html**
```

<a href="projects.html**[COLOR="DarkGreen"]?proj=1[/COLOR]**"><img src="image1.jpg"></a>
<a href="projects.html**[COLOR="DarkGreen"]?proj=2[/COLOR]**"><img src="image2.jpg"></a>
<a href="projects.html**[COLOR="DarkGreen"]?proj=3[/COLOR]**"><img src="image3.jpg"></a>

```

**NB:**
*****project1.jpg and project2.jpg and project3.jpg are NOT visible at all times on the **projects.html** page. They are visible only WHEN CALLED - one at a time - by the **display_project()** function.
*****the goal is to be able to click on one of the imageX.jpg links on **index.html** and be brought to **projects.html** with the relevant projectX.jpg image displayed (on **projects.html**) - essentially, looking for a way to BOTH navigate to **projects.html** from **index.html** AND trigger **display_project()** with **index.html** generated parameters ( i.e. **display_project(1)** or **display_project(2)** or **display_project(3)** set), simultaneously...

**Possible solution:**
[ **[COLOR="DarkGreen"]query strings[/COLOR]** ]("http://javascript.about.com/library/blqs.htm")

Will report back!

Thanks for any additional wisdom!

---

### Post by SeijiSensei on 2012-05-18
I'd make the project page a PHP script and pass the project number as a parameter like you did above:

```

<a href="projects.php?proj=1"><img src="image1.jpg"></a>

```

would then generate a page where the appropriate content for project 1 would be displayed.  Even a simple script like this would work:

```

<?php

#anti-spoofing
if (!is_numeric($_GET['proj'])) { 
    echo "Go away!";
    exit;
}

$myproject="/path/to/projects/project".$_GET['proj'].".html";

if (!file_exists($myproject)) {
    echo "Cannot find project!";
    
} else {
    include($myproject);

}

?>

```

That would display the contents of the file project1.html in the directory "/path/to/projects". The "www-data" user that Apache runs as would need read and execute privileges in /path/to/projects.

---

### Post by maclenin on 2012-05-18
**SeijiSensi!**

In my particular case, it was laughingly simple (as currently described) - using **[COLOR="DarkGreen"]query strings[/COLOR]**, indeed:

**index.html**
<a href="projects.html**[COLOR="DarkGreen"]?proj=1[/COLOR]**"><img src="image1.jpg"></a>
<a href="projects.html**[COLOR="DarkGreen"]?proj=2[/COLOR]**"><img src="image2.jpg"></a>
<a href="projects.html**[COLOR="DarkGreen"]?proj=3[/COLOR]**"><img src="image3.jpg"></a>

**projects.html**
<body onload="display_project(1);">

**projects.js**
function display_project(p)
{
**[COLOR="DarkGreen"]if (window.location.search.charAt(6)) {p=window.location.search.charAt(6);}[/COLOR]**
document.getElementById("project").src="project"+p+".jpg";
}

**Thanks, all, for the help!**

Fruitful **[COLOR="DarkGreen"]query string[/COLOR]** references:
[one]("http://stackoverflow.com/questions/3656068/how-do-i-preserve-variable-values-between-html-files")
[two]("http://javascript.about.com/library/blqs.htm")
[three]("https://developer.mozilla.org/en/DOM/window.location")

---

