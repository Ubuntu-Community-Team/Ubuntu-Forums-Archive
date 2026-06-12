---
title: "CONSTANTS not working in specified manner - PHP 5.3.8"
date: 2011-09-03
forum: Programming Talk
---

### Post by etdsbastar on 2011-09-03
Hello there,

I would really appreciate if someone will help me regarding this, since I am getting frustrated from the past 2 days, finding a solution for this.

I am creating a project in PHP, having various directory structures and files.

1. ROOT folder contains index.php having contents as:

```

<?php define('BASEPATH', dirname(__FILE__) . '/');
define('BASEURL', substr($_SERVER['PHP_SELF'], 0, - (strlen($_SERVER['SCRIPT_FILENAME']) - strlen(BASEPATH))));
require_once ( BASEPATH . 'includes/core.php' ); ?>

```

2. There is another folder INCLUDES under ROOT having other files naming:

[LIST]
[*]common.php
[*]core.php
[*]error.php
[*]functions.php
[/LIST]
3. Contents of core.php is:

```

<?php // require_once config.php
if ( file_exists(BASEPATH . 'config.php') )
    require_once( 'config.php' );
else
    die ( 'Master configuration file not found, can\'t continue.' );

// Include common sessions file
if ( file_exists(BASEPATH . 'includes/common.php') )
{
    require_once( 'common.php' );
}
else
{
    die ( 'Common include file not found. Possible location: ' . BASEPATH . 'includes/common.php' );
}

// require_once functions.php
if ( file_exists(BASEPATH . 'includes/functions.php') )
    require_once( 'functions.php' );
else
    die ( 'Functions file not found, can\'t continue.' );

// Include common library file
if ( file_exists(BASEPATH . 'lib/classes.php') )
{
    require_once( BASEPATH . 'lib/classes.php' );
}
else
{
    die ( 'Common library file not found. Possible location: ' . BASEPATH . 'lib/classes.php' );
}

// Create a new instance of DB class.
$_DB = new DB;

if ( file_exists( BASEPATH . 'template/index.php' ) )
    html_header_location ( 'template/index.php' );
else
    die ( raise_error('03') );

?>

```

4. Now, here is what the problem arises with other included files, All of the included files are giving me the error/warning:

```

Notice: Use of undefined constant BASEPATH - assumed 'BASEPATH' in /home/abc/server/csm/template/index.php

```

I don't know why the constant's are not working in other files / files residing in other directories and THE CONSTANT BASEPATH HAS BEEN DECLARED IN THE ROOT FILE (INDEX.PHP) already.

Please help.

---

### Post by etdsbastar on 2011-09-03
This code is also not working as expected which is under ROOT/TEMPLATE folder:

```

<?php
    echo "<pre>";
        $test = $_DB->Query("select * from employee");
        print_r ($test);
    echo "</pre>";
    exit();
?>

```giving me the error:

```

Notice: Undefined variable: _DB in /home/abc/server/csm/template/index.php on line 3  Fatal error: Call to a member function Query() on a non-object in /home/abc/server/csm/template/index.php on line 3 
```$_DB has already been defined. See the master post above.

**$_DB = new DB;**

---

### Post by etdsbastar on 2011-09-04
Changed all of the coding but still no success.

---

### Post by etdsbastar on 2011-09-04
Is there anyone who can help me.

---

### Post by etdsbastar on 2011-09-05
is there anyone to help me....

---

