---
title: "html5 &amp; css3 break when change to php"
date: 2014-06-06
forum: Programming Talk
---

### Post by greg54 on 2014-06-06
I am trying to use php for my header, nav, sidebars and footer. When i put them into their .php file and change the index file from the old div to the <?php include('includes/header.php'); ?> everything disappears. Thoughts? I am a newbie so i might be overlooking something simple.

In my main folder i have all the .html files as well as a main.php and an index.php file. I have two folders, includes and variables, where the rest of the .php files are located.

Here is my index.php file ( i will put my original index.html below)

```
<!doctype html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <Title>title</title>
    <link rel="stylesheet" href="main.css" type="text/css"/>
    <meta name="viewport" content="width-device-width, initial-scale=1.0>
</head>


<body class="body">
<div id="pageCenter">


    <?php include('includes/header.php'); ?>    
        
    <?php include('includes/nav.php'); ?>




    <div class="mainContent">
        <div class="content">
            <article class="topcontent">
                <header>
                    <h2><a href="#" title="First Post">Welcome to our site!</a></h2>
                </header>
                
                <content>
                    <p></p>
                </content>
            
            </article>
            
            <article class="midcontent">
                <header>
                    <h2><a href="#" title="Second Post">Second Post</a></h2>
                </header>
                
                <footer>
                    <p Class="post-info"> This post is written by Mike.</p>
                </footer>
                
                <content>
                    <p>gaghalj agjoha g ajkgha l ajkogh ajklakg ahg a .</p>
                </content>
            
            </article>
            
            <article class="bottomcontent">
                <header>
                    <h2><a href="#" title="Third Post">Third Post</a></h2>
                </header>
                
                <footer>
                    <p Class="post-info"> This post is written by Bill.</p>
                </footer>
                
                <content>
                    <p>gaghalj agjoha g ajkgha l ajkogh ajklakg ahg a .</p>
                </content>
            
            </article>
            
        </div>
    </div>


    
    
    <?php include('includes/topSidebar.php'); ?>
    <?php include('includes/middleSidebar.php'); ?>
    <?php include('includes/bottomSidebar.php'); ?>


    <?php include('includes/footer.php'); ?>
    
</div>
</body>
</html>
```

--------------------------------index.html------------------

```
<!doctype html>
<html lang="en">
<head>
    <meta charset="utf-8" />
    <Title>title</title>
    <link rel="stylesheet" href="main.css" type="text/css"/>
    <meta name="viewport" content="width-device-width, initial-scale=1.0>
</head>


<body class="body">
<div id="pageCenter">


    <header class="mainHeader">
        <center><img src="pictures/40mmBanner.jpg"></center>
    </header>    
        
        <nav><ul class="menu">
        </nav>




    <div class="mainContent">
        <div class="content">
            <article class="topcontent">
                <header>
                    <h2><a href="#" title="First Post">Welcome to our site!</a></h2>
                </header>
                
                <content>
                    <p></p>
                </content>
            
            </article>
            
            <article class="midcontent">
                <header>
                    <h2><a href="#" title="Second Post">Second Post</a></h2>
                </header>
                
                <footer>
                    <p Class="post-info"> This post is written by Mike.</p>
                </footer>
                
                <content>
                    <p>gaghalj agjoha g ajkgha l ajkogh ajklakg ahg a .</p>
                </content>
            
            </article>
            
            <article class="bottomcontent">
                <header>
                    <h2><a href="#" title="Third Post">Third Post</a></h2>
                </header>
                
                <footer>
                    <p Class="post-info"> This post is written by Bill.</p>
                </footer>
                
                <content>
                    <p>gaghalj agjoha g ajkgha l ajkogh ajklakg ahg a .</p>
                </content>
            
            </article>
            
        </div>
    </div>


    
    
    <aside class="top-sidebar">
        <article>
            
        </article>
    </aside>
    <aside class="middle-sidebar">
        <article>
            
            
        </article>
    </aside>
    <aside class="bottom-sidebar">
        <article>
            <h2>Bottom Sidebar</h2>
            <p>sdfjkla asdfjkl sdfjkl;a jklsdf sdfjkl;</p>
        </article>
    </aside>
    
    
    
    <footer class="mainFooter">
        <p>Copyright &copy: 2014 </p>
    </footer>
    
</div>
</body>
</html>
```

---

### Post by Duncubuntu on 2014-06-07
Can you show me your full folder structure, or as much that is relevant as you can? Do you have proper permissions on your folder structure? (755 for folders and 644 files)?

---

### Post by Duncubuntu on 2014-06-07
Also in HTML5 you do not need to specify type for css, so this:
```
    <link rel="stylesheet" href="main.css" type="text/css" />

```

Can become this:
```
    <link rel="stylesheet" href="main.css" />

```

This is a small optimization, but every bit counts!

---

### Post by Duncubuntu on 2014-06-08
Where is your pictures folder? This might be causing you problems:

```
<center><img src="pictures/40mmBanner.jpg"></center>
```

You may need to change it to the following if your pictures folder is in the same folder as includes and variables, your "base" folder:

```
<center><img src="../pictures/40mmBanner.jpg"></center>
```

The "../" basically means start from parent directory.

*EDIT* And sorry maybe this is a silly question, but do you have a server installed? How are you viewing this site?

---

### Post by greg54 on 2014-06-09
all of my files are in the 40mm folder. I have the pictures folder in the 40mm file as well. I just have this locally on my PC right now using notepad++ so the folder is at C:/greg/notepad++/40mmradio/pictures. When I use my normal .html file everything looks fine but when I try to transfer the reusable items to php those items disappear. I use ipage for my hosting, should I upload the new .php files there and see if it works? Would there be a differance in that and the demo from notpad++?

---

### Post by greg54 on 2014-06-09
> **Duncubuntu said:**
> Also in HTML5 you do not need to specify type for css, so this:
```
    <link rel="stylesheet" href="main.css" type="text/css" />

```

Can become this:
```
    <link rel="stylesheet" href="main.css" />

```

This is a small optimization, but every bit counts!


Thanks!

---

### Post by greg54 on 2014-06-09
I uploaded the .php files to my host...and it works. I am sorry for wasting your time. I just thought that if it did not work on notepad++ then it would not work in production. Do you know why this is? Again, sorry and thank you.

---

### Post by SeijiSensei on 2014-06-09
Do you mean they "didn't work" when looked at in an editor?  PHP files require a parser to take the code and produce the rendered output.  Web servers with PHP enabled perform this task.  An editor will simply show you the code.

---

### Post by greg54 on 2014-06-09
Yes, in the editor the PHP did not work but when uploaded to ipage everything worked. Thanks for the clarification.

---

### Post by Duncubuntu on 2014-06-13
If you want faster development, look into setting up Virtual Box, install your choice of distro on there, and get an apache server going. Or do a basic LAMP install. This way you can just edit files locally, and get results faster. Saves bandwidth too ;)

---

### Post by CharlesA on 2014-06-13
> **Duncubuntu said:**
> If you want faster development, look into setting up Virtual Box, install your choice of distro on there, and get an apache server going. Or do a basic LAMP install. This way you can just edit files locally, and get results faster. Saves bandwidth too ;)

+1. That's exactly what I do when working on my site.

---

