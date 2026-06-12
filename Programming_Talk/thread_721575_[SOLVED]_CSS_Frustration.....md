---
title: "[SOLVED] CSS Frustration...."
date: 2008-03-11
forum: Programming Talk
---

### Post by The Titan on 2008-03-11
This wont clear floated elements and i don't know why.  Probably very stupid i just need another set of eyes.

css:

```

body{
    background-color:#EFF2F3; 
     text-align:center;
}
#site_container{
    margin:auto;
    width:970px;
    margin-top:45px;

}
#main_top{
    width:970px;
    height:40px;
    background-image:url("images/top.png");
    
}
#main_middle{
    width:970px;
    background-image:url("images/middle.png");
    background-repeat:repeat-y;

}
#main_bottom{
    width:970px;
    height:40px;
    background-image:url("images/bottom.png");
    clear:both;
}

#header{

    height:110px;
    width:940px;
    background-image:url("images/header.png");
    margin-left:15px;
    margin-right:15px;
}

#menubar{
    background-color:black;
    float:left;
    width:100px;

}

#content{
    background-color:black;
    float:right;
    width:100px;
}
#cont_container{
    width:940px;
    padding-left:15px;
    padding-right:15px;
    height:10px;
    clear:both;

}

```HTML:
[html]
<html>
    <head><link href=\"{$stylesheet}\" rel=\"stylesheet\" type=\"text/css\" />
    <title>Powered By: FireWare CMS Alpha v 0.0.5</title></head>
        <body>
            <div id=\"site_container\">
                <div id=\"main_top\">&nbsp;</div>
                <div id=\"main_middle\">&nbsp;
                    <div id=\"header\">&nbsp;</div>
                    <div id=\"cont_container\">
                        <div id=\"menubar\">&nbsp;</div>
                        <div id=\"content\">&nbsp;</div> 
                    </div>
                
                </div>
                <div id=\"main_bottom\">&nbsp;</div>
            </div>
    </body>
</html>
[/html]Its the "cont_container" that wont stretch out and i dont know why.... (please ignore the escape characters, i don't feel like deleting them all)

visit: [http://97.112.75.13/fw/trunk/home.php](http://97.112.75.13/fw/trunk/home.php)  to see whats happening.

---

### Post by Can+~ on 2008-03-11
I downloaded your whole site into my apache server and I'm working on it btw, impossible to edit html without knowing.

*edit*
Fixed, you should set float to everything inside the css, set the main_middle float to left so it will expand the area, and all sub-divs with proper floating and position:fixed for every div as default.

---

### Post by The Titan on 2008-03-11
> **Can+~ said:**
> on main_middle set overflow:auto; so the background can repeat instead of hiding itself.

I downloaded your whole site into my apache server and I'm working on it btw, impossible to edit html without knowing.

Still working on your issue.
you seem like you know your way around a web site.  Are you interested in helping with this project?

its impossible to edit html whtout knowing what?

---

### Post by Can+~ on 2008-03-11
> **The Titan said:**
> you seem like you know your way around a web site.  Are you interested in helping with this project?

its impossible to edit html whtout knowing what?

Knowing how it looks, that's why I copied into my /www/ folder. Anyway, I edited my previous comment with the solution, divs are bitches, they need to be set to static and floated properly, otherwise they won't expand as intended.

And I don't know what your project is about.

---

### Post by The Titan on 2008-03-11
Check your PM's!

---

### Post by Can+~ on 2008-03-11
This is a html layout, go ahead and use it.

---

