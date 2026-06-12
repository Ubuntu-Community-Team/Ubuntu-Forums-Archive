---
title: "HTML/CSS Horizontal Menu Help!"
date: 2009-08-22
forum: Programming Talk
---

### Post by Mizutsuki on 2009-08-22
Hello,
I'm trying to write a web page for a martial arts dojo, and I'm having trouble producing the desired effect in IE6 and IE7.  Bear in mind that IE8, FF3.0 and FF3.5 render the page the exact same and are pretty much what I want.

I used a couple of different guides to produce this:

```
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=iso-8859-1">
        <style type="text/css">
        <!-- 
		
		#menu {
            list-style: none;
            padding: 0;
            border: none;
            margin: 0;
        }
        
        #menu img {
            border: none;
        }
        
        #menu li {
            float: left;
        }
        
        #menu li a {
            display: inline;
        }
        
        #menu li ul {
            position: absolute;
            display: none;
            list-style: none;
        }
        
        #menu li:hover ul, li.over ul {
            display: block;
            position: absolute;
        }
        
        #menu li ul li {
            display: inline;
            float: left;
        }
        
        /* Fix IE. Hide from IE Mac \*/ 
		* html ul li {
            float: left;
        }
		
		* html ul li a {
            height: 1%;
        }
        /* End */
		
        -->
        </style>
        <script type="text/javascript">
            <!--
            //--><![CDATA[//><!--
            startList = function(){
                if (document.all && document.getElementById) {
                    navRoot = document.getElementById("menu");
                    for (i = 0; i < navRoot.childNodes.length; i++) {
                        node = navRoot.childNodes[i];
                        if (node.nodeName == "LI") {
                            node.onmouseover = function(){
                                this.className += " over";
                            }
                            node.onmouseout = function(){
                                this.className = this.className.replace(" over", "");
                            }
                        }
                    }
                }
            }
            window.onload = startList;
            //--><!]]>
        </script>
        <title>Test</title>
    </head>
    <body>
    	<div style="width:1370px;">
        <ul id="menu">
            <li>
                <a href="/"><img alt= "home" name="button-home" src="uploadable images/bars/homedown.gif" onmouseover="this.src='uploadable images/bars/homedown.gif';" onmouseout="this.src='uploadable images/bars/homedown.gif';"/></a>
                <ul>
                    <li>
                        <a href="home/about.html"><img alt="about" src="uploadable images/about-about.gif"/></a>
                    </li>
                    <li>
                        <a href="home/instructor.html"><img alt="instructor" src="uploadable images/about-instructor.gif"/></a>
                    </li>
                    <li>
                        <a href="home/classes.html"><img alt="classes" src="uploadable images/about-classes.gif"/></a>
                    </li>
                </ul>
            </li>
            <li>
                <a href="Seibujan Jujutsu/index.html"><img alt="Seibukan Jujutsu" src="uploadable images/bars/sjup.gif" onmouseover="this.src='uploadable images/bars/sjover.gif';" onmouseout="this.src='uploadable images/bars/sjup.gif';"/></a>
                <ul>
                    <li>
                        <a href="Seibujan Jujutsu/history.html"><img alt="history" src="uploadable images/sj-history.gif"/></a>
                    </li>
                    <li>
                        <a href="Seibujan Jujutsu/philosophy.html"><img alt="philosophy" src="uploadable images/sj-philosophy.gif"/></a>
                    </li>
                    <li>
                        <a href="Seibujan Jujutsu/founder.html"><img alt="founder" src="uploadable images/sj-founder.gif"/></a>
                    </li>
                </ul>
            </li>
            <li>
                <a href="Events Calendar/index.html"><img alt="events" src="uploadable images/bars/eventsup.gif" onmouseover="this.src='uploadable images/bars/eventsover.gif';" onmouseout="this.src='uploadable images/bars/eventsup.gif';"/></a>
            </li>
            <li>
                <a href="Media/index.html"><img alt="media" src="uploadable images/bars/media.gif" onmouseover="this.src='uploadable images/bars/mediaover.gif';" onmouseout="this.src='uploadable images/bars/media.gif';"/></a>
                <ul>
                    <li>
                        <a href="Media/videogallery.html"><img alt="video" src="uploadable images/media-video.gif"/></a>
                    </li>
                    <li>
                        <a href="Media/photogallery.html"><img alt="photo" src="uploadable images/media-photo.gif"/></a>
                    </li>
                    <li>
                        <a href="Media/policy.html"><img alt="policy" src="uploadable images/media-policy.gif"/></a>
                    </li>
                </ul>
            </li>
            <li>
                <a href="Testimonials/index.html"><img alt="testimonials" src="uploadable images/bars/testup.gif" onmouseover="this.src='uploadable images/bars/testover.gif';" onmouseout="this.src='uploadable images/bars/testup.gif';"/></a>
            </li>
            <li>
                <a href="Contact/index.html"><img alt="contact" src="uploadable images/bars/contactup.gif" onmouseover="this.src='uploadable images/bars/contactover.gif';" onmouseout="this.src='uploadable images/bars/contactup.gif';"/></a>
            </li>
            <li>
                <img alt="" src="uploadable images/bars/end.gif"/>
            </li>
        </ul>
        </div>
    </body>
</html>
```

My problem is that in IE6 the sub-menus do not show.  Unfortunately I don't understand JS very well, but the function above came from a [tutorial]("http://www.alistapart.com/articles/horizdropdowns/").  Is there anyone who can help me to understand how to make the menus appear?

Thank you

---

### Post by tturrisi on 2009-08-23
[http://css.maxdesign.com.au/listamatic/](http://css.maxdesign.com.au/listamatic/)

---

### Post by hessiess on 2009-08-23
[http://www.grc.com/menu2/invitro.htm](http://www.grc.com/menu2/invitro.htm)

---

