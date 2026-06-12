---
title: "PHP code improvement"
date: 2007-09-18
forum: Programming Talk
---

### Post by md5hash on 2007-09-18
can anyone improve this coding 

**index.php**
[PHP]
if (!file_exists('config.php')) 
	die("Missing config file...");
	
require('config.php');

call_user_func(main());

function main() {
	if (empty($_REQUEST['page'])) {
		require_once('sources/index.php');
		return 'index';
	}
	
	$arrPage = array (
		'newitem' => array('items.php','newItem')
	);
	
	require_once('sources/'.$arrPage[$_REQUEST['page']][0]);
	return $arrPage[$_REQUEST['page']][1];
}
[/PHP]

**items.php**
[PHP]
function newitem() {
       return "<html><h1>new item</h1></html>";
}

function Delitem() {
       return "<html><h1>delete item</h1></html>";
}

[/PHP]

---

### Post by mssever on 2007-09-18
Why not replace [php]call_user_func(main());[/php] with [php]main();[/php]?

---

### Post by md5hash on 2007-09-18
because pages will be accessed from this form 

[http://localhost/index.php?action=newitem](http://localhost/index.php?action=newitem)
[http://localhost/index.php?action=delitem](http://localhost/index.php?action=delitem)

did you get it?

---

### Post by mssever on 2007-09-18
If you had done something like [php]//sanitize $_GET['action'];
call_user_func($_GET['action']);[/php]I would understand it. As it stands, though call_user_func() always calls main(), so you might as well call main() directly.

EDIT: You can also use variable function calls to shorten your code. For example:
[php]$foo = 'main';
$foo();[/php]

---

### Post by Keymone on 2007-09-18
you are a bit wrong. call_user_func will call function which name is the return value of main().

this code can be improved a bit, here is what i came with:

[php]
function main() {
    $arrPage = array (
        'newitem' => array('items.php','newItem'),
        'delitem' => array('items.php', 'delitem'),
        'default' => array('index.php', 'index')
    );
  
   $page = $_REQUEST['page'];
    
    if( array_key_exists( $page, $arrPage ) ) {
        require_once('sources/'.$arrPage[$page][0]);
        return $arrPage[$page][1];
    } else {
        require_once('sources/'.$arrPage['default'][0]);
        return $arrPage['default'][1];
    }
}
[/php]

i'm not sure if array_key_exists is the right functuion with right syntax because i was not using PHP for a year or so but i hope you get the point

---

### Post by md5hash on 2007-09-18
thanks for that.. anymore?

---

### Post by Keymone on 2007-09-18
i do not know what exactly do you want from that code :) you can also write a PHP extension in C++ with ASM inclusions - this would help you with performance issue ;)

---

### Post by md5hash on 2007-09-18
can it evolve into a simple mvc?

---

### Post by Keymone on 2007-09-18
well i do not see any signs of Views or Models.. but yes - everything can evolve into MVC :)

---

