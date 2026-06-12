---
title: "More CSS issues..."
date: 2009-12-15
forum: Programming Talk
---

### Post by gjoellee on 2009-12-15
I notice I have not done this for a while...

I am trying to add a background color to a logo section on me website. I am keeping the website online so you can see: [www.stupidreality.org](www.stupidreality.org) (the empty section need a background, as well as an image which will be the logo).

See
```
#logo
```
in the txt file attached.

The problem is that the background color does not appear, and how to I add an image on top of the background color?

---

### Post by Physical Hook on 2009-12-15
logo div width should be at least 1px wide to be visible.

[[IMG]http://i48.tinypic.com/20k2mgw_th.png[/IMG]]("http://i48.tinypic.com/20k2mgw.png")

---

### Post by gjoellee on 2009-12-15
> **Physical Hook said:**
> logo div width should be at least 1px wide to be visible.

[[IMG]http://i48.tinypic.com/20k2mgw_th.png[/IMG]]("http://i48.tinypic.com/20k2mgw.png")

Width is indeed the problem. Tried setting:
```
width: auto;
```
and nothing happened.

If i set:
```
width: 600px;
```
i get 600px with the color #343434. 

Still why does not width: auto; work? It will just look weird on many resolutions if i set width: 1900px;

This is what the section looks like now:
```
#logo {
	float: left;
	background: #343434 repeat-x;
	height: 80px;
	width: auto;
}
```

---

### Post by Physical Hook on 2009-12-15
[COLOR=Green]width: auto;[/COLOR] will adjust the width depending on the div contents and/or it's parent. Since the div is empty, you get nothing ( 0px ).

---

### Post by gjoellee on 2009-12-15
Maybe I should have given the fact that I am currently on a CMS...Drupal. I am not sure of how I am supposed to fill in something in the div.

EDIT:
Here is the div:
```
<div id="logo">
          <?php if ($logo || $site_name) {
            print '<a href="'. check_url($base_path) .'" title="'. $site_name .'">';
            if ($logo) {
              print '<img src="'. check_url($logo) .'" alt="'. $site_name .'" />';
          } else {
            print '<span id="sitename">'. $site_name .'</span>';
          }
            print '</a>';
          }
        ?>
        <?php if ($site_slogan): print '<div id="tagline">'. $site_slogan .'</div>'; endif; ?>
        </div>
```

---

### Post by Reiger on 2009-12-15
There is min-width if you must force an element to fit a width constraint; similarly max-width, min-height and max-height.

I am not 100% sure about the effect those have on empty elements, though.

---

### Post by gjoellee on 2009-12-15
> **Reiger said:**
> There is min-width if you must force an element to fit a width constraint; similarly max-width, min-height and max-height.

I am not 100% sure about the effect those have on empty elements, though.

Does not seem to work in this case...

---

### Post by Physical Hook on 2009-12-15
[PHP]if ($logo) {
    print '<img src="'. check_url($logo) .'" alt="'. $site_name .'" />';
} else {
    print '<span id="sitename">'. $site_name .'</span>';
}
[/PHP]

Haven't used Drupal but something is definitely wrong here. Regardless of the result of this if / else statement, logo div should contain at least an incomplete image declaration or an empty span :-k

---

### Post by gjoellee on 2009-12-16
I am using a temporary fix by setting: ```
width: 1900px;
```.

This does however cause a horizontal scrollbar to appear in your browser, and on high resolutions the top looks weird. It anyways look quite normal for most people.

---

### Post by gjoellee on 2009-12-16
Still any ideas of how to really fix the problem?

---

### Post by Physical Hook on 2009-12-16
> **gjoellee said:**
> I am using a temporary fix by setting: ```
width: 1900px;
```.

This does however cause a horizontal scrollbar to appear in your browser, and on high resolutions the top looks weird. It anyways look quite normal for most people.

I would go for 99% .. At least it'll ( to a certain level ) adjust itself to various resolutions.

---

### Post by gjoellee on 2009-12-16
> **Physical Hook said:**
> I would go for 99% .. At least it'll ( to a certain level ) adjust itself to various resolutions.

Does not work exactly as I want it to, but i guess it is better with the thought of resolution. It is a better fix, but still it can be better!

---

### Post by gjoellee on 2009-12-19
Bump

---

### Post by Can+~ on 2009-12-19
I usually pull a little trick for this kind of things. I have a repeating background defined on the whole page, and then the logo is placed over it, but designed so that it blends entirely with the logo.

The width:100% or 99% works only when there are no elements around causing either padding:, margin: or even border:. So if you still want to do it this way, you'll have to get rid of any of them.

---

