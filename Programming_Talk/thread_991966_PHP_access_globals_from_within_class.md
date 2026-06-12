---
title: "PHP access globals from within class"
date: 2008-11-24
forum: Programming Talk
---

### Post by mike_g on 2008-11-24
I have a class that basically just holds a set of functions within the classes namespace. I have some globals set in a configuration file. My problem is that I cant seem to access the globals from within the scope of my class; however, I dont seem to have a problem accessing Joomla variables so there must be something that I am doing wrong. Heres a reduced example of my code:
```

$myGlobalVar = 10;
comCompo::printGlobal();

class comCompo
{
    function printGlobal()
    {
        global $myGlobalVar;
        echo $myGlobalVar; // <- does nothing
    }
} 
```

---

### Post by dgoosens on 2008-11-24
this is quite logic actualy...
classes aren't functions... they don't know what happens outside their instances...

EDIT: this would not work with functions either...

You should do something like this:

```

<?php

class comCompo
{
    private $globalVar = 10;

    public function printGlobal()
    {
        print $globalVar;
    }
}

comCompo::printGlobal();

?>

```

but this class doesn't make a lot of sense...
you might want to add a constructor or a set function otherwise you will not be able to modify $globalVar

```

<?php

class comCompo
{
    private $globalVar = 10;  //10 being the default value

    public function __constructor($globalVar)
    {
        $this->globalVar = $globalVar;
    }

    public function printGlobal()
    {
        print $globalVar;
    }
}

comCompo::printGlobal();    // will output '10'

//or
$myGlobalVar = new comCompo(15);
$myGlobalVar->printGlobal();   // will output '15'

?>

```

---

### Post by mike_g on 2008-11-24
Thanks for the reply. I was hoping to be able to avoid having to create an instance of my class as I'm calling functions from it like: comCompo::printGlobal(); all over the place and it would require making changes to all the calls. I guess that if this is the only way to go about this then making the changes sooner would be better than later.

---

### Post by dgoosens on 2008-11-24
in that case, just start a session and set a variable...

```

<?php

session_start();

$_SESSION['globalVar'] = 10;

?>

```

then you can simply access this directly or with a function as long as the session remains active...

```

function printGlobalVar()
{
	print_r($_SESSION['globalVar']);
}

printGlobalVar();

//or

print_r($_SESSION['globalVar']);

```

---

### Post by mike_g on 2008-11-24
Lol, yeah nice idea. Why dident I think of that? >_<

---

### Post by dgoosens on 2008-11-24
i know...

always keep in mind 
KISS = Keep It Simple Stupid !

---

### Post by drubin on 2008-11-24
> **mike_g said:**
> 

Also note that sessions are used for persistent storage and not for global vars.

[Sessions]("http://www.php.net/manual/en/session.examples.php")
[Global]("http://www.php.net/global")

---

