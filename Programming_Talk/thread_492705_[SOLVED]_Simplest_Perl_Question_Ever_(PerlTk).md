---
title: "[SOLVED] Simplest Perl Question Ever (Perl/Tk)"
date: 2007-07-05
forum: Programming Talk
---

### Post by MrFSL on 2007-07-05
This is driving me crazy!

Using Perl/Tk

I want to create a window and size it to a default width and height.

```

#!/usr/bin/perl

use Tk;

$MW = MainWindow->new(-title=>'AppName'-width=>'600',-height=>'600');
MainLoop();

```

This does not work. The Main Window is only as big as the widgets I put inside it! What am I doing wrong? I can configure the size of any other Toplevel in this way. It's driving me nuts. Someone please set me straight!

Thanks,
MrFSL

---

### Post by Modred on 2007-07-05
```
$MW = MainWindow->new(-title=>'-width=>'600',-height=>'600');
```
Simple syntax issue.  You didn't close the title string or separate it from the width.
```
$MW = MainWindow->new(-title=>'Title',-width=>'600',-height=>'600');
```
The second one works fine for me.

---

### Post by MrFSL on 2007-07-05
Sorry... typo...

That is exactly what I have.

```

$MW = MainWindow->new(-title=>'AppName',-width=>'600',-height=>'600');

```

The problem is that this script will open a window with an area 600x600... GREAT! but as soon as I add a widget:

```

$MW = MainWindow->new(-title=>'AppName',-width=>'600',-height=>'600');
$MW->Label(-titlet=>'AppName')->grid(-row=>0,-column=>0);

```

The MainWindow resizes to the size of the widget!!!!!

Please Somebody Help... I have been racking my brain on this one forever!

Thanx

---

### Post by Modred on 2007-07-05
Use place() not grid().

Grid() automatically manages your window for you, but place() lets you define exactly where you want things to go.

```
$MW->Label(-text=>'AppName')->place(-x=>0,-y=>0);
```

---

### Post by MrFSL on 2007-07-05
OMG you ROCK!

I was familiar with 'grid' and 'pack' but this is a first for 'place'

And the greatest part is that it works so freakin simple!!!!!

Modred... I owe ya!

**Off Topic Note**
Funny I can get a perl question answered on the Ubuntu Forums before I can get it answered anywhere else!

---

### Post by Modred on 2007-07-05
[http://www-users.cs.umn.edu/~amundson/perl/perltk/toc.html](http://www-users.cs.umn.edu/~amundson/perl/perltk/toc.html)

Thought I'd throw in the reference I used for good measure.

---

### Post by MrFSL on 2007-07-05
Thank you again... for additional good measure I would like to note:

```
**$MW->gridPropagate(0);**
```

If you wish to use 'grid' as your geometry manager then the above will keep the Main Window from resizing when adding widgets. likewise if using 'pack':

```
**$MW->packPropagate(0);**
```

Final code looks like:

```

[B]$MW = MainWindow->new(-title=>'AppName',-width=>'600',-height=>'600');
$MW->gridPropagate(0);
$MW->Label(-title=>'AppName')->grid(-row=>0,-column=>0);
[/B]
```

---

### Post by MrFSL on 2007-07-07
This also works:

```

$MW = MainWindow->new(-title=>'AppName');
$MW->geometry('600x600');
$MW->Label(-title=>'AppName')->grid(-row=>0,-column=>0);

```

---

