---
title: "Roll Your Own PHP Framework"
date: 2009-05-28
forum: Programming Talk
---

### Post by SuperMike on 2009-05-28
Lately I've been experimenting with my very own MVC framework in PHP. I thought I'd share the technique. One major goal of doing your own custom framework of course is to fend off criticism about building yet again another framework. So, if you build one, the point about what you do inside it should be completely obvious. A newbie dev who inherits your code should be able to jump in and get going fairly quickly.

If you're not familiar with what MVC is, here it is:

[http://en.wikipedia.org/wiki/Model-view-controller](http://en.wikipedia.org/wiki/Model-view-controller)

Basically you are separating your PHP from your PHP + SQL from your XHTML/CSS, and you're providing pretty URLs, and often are loading some common classes you'll often use on projects. Another key point about MVC is the whole way of doing Gang of Four or EAI refactoring under "models", but that's another topic for another day. You can read up on the topic by googling on refactoring.

And another thing that threw me for a loop was the naming. Just think this:

front controller = the central point of access to the website, no matter which URL is typed, and it routes to the page controllers

page controllers = kind of like a skeleton page that loads your models with data, gets data off the models, and sends it to the page templates (views)

models = this was hard for me to grasp why it's called models, but basically it's where the meat of all your code should go so that you have code reuse instead of cut and paste. Just forget that it's called models. Think of it just simply called "classes", even though it's not named that.

views = just replace the notion of "page templates" with "views".

Usually these things start with what's called a front controller. It's basically the central hub where all URL requests come into your website. You might call it index.php, but it's more than just that. You first make an Apache .htaccess file that has something like this in it:

```
RewriteEngine On
RewriteCond %{REQUEST_FILENAME} !-f
RewriteCond %{REQUEST_FILENAME} !-d
RewriteRule . /index.php [QSA]
```

What this does is basically take all 404s, where someone has typed in any URL at all for files that might not exist on the website, and route them all through index.php before it actually does a 404. We call this the pretty url front controller technique. Note that this technique does not cause Google's spider index system to register the site as one great big 404. If you had had use the Apache2 ErrorDocument 404 directive technique for this, then you most certainly would have -- so I don't recommend that. Use the ErrorDocument directive appropriately -- for handling anything that you send a 404 header on from your PHP code.

Then, in index.php, you'll want to load a bootstrap.php that loads your framework, and then parse the incoming URL, and then route out the request to what's called a page controller. But first, let's discuss the obvious directory structure:

```
.htaccess
404.html
robots.txt
site.conf
index.php
controllers/
controllers/Home/Home.php
models/
views/
views/Home/vHome.php
system/
system/bootstrap.php
system/static_Controller.php
system/static_View.php
system/static_Model.php
system/static_Settings.php
```

I actually think this is pretty obvious in how this works if you actually know how to use an MVC.

You see, with this, you get your page controllers under "controllers", your models under "models", your view templates under "views", and the framework classes under "system". This makes it pretty obvious to recognize and use.

As well, you get static classes that let you do controller work with static_Controller.php, model work with static_Model.php, and view work with static_View.php.

And the Home/Home.php page controller would be the controller that handles when someone hits your site like:

```
http://mysite.com/
```

And the Home/vHome.php view template would be the view you can call from your page controller Home/Home.php so that you show your XHTML. And the reason I used the vHome instead of Home? Yeah -- it's so when editing files you don't get the text editor (IDE) tabs confused and you know therefore that this is a view template file.

The job of bootstrap.php should be to load your common static framework classes and other common classes (non-static) out of the "system" folder -- thereby making all your pages already have those classes in memory. You can also put some instantiation code at the bottom of these common classes so that you don't need to instantiate them.

Okay, now going back to the index.php, which is your front controller, take a cue from the CodeIgniter. In CI, you can create a folder structure like this:

```
controllers/EmployerSettings/Update.php
```

and automatically call it without having to edit your front controller (index.php) like so:

```
http://mysite.com/employer-settings/update/
```

And, as a bonus, you can do:

```
http://mysite.com/employer-settings/update/2323023/ABCDE/
```

...and the Update.php file can receive the stuff after /update/ by parsing for this and using it as necessary.

Pretty slick, huh? Well, what makes that possible is that you parse the incoming URL, apply some rules on the string, prevent XSS and do other security controls, and then use require_once() to load that file. So, the general format for URLs would be:

```
http://mysite.com/{Domain Object}/{Task}/{whatever}/{whatever}
```

So that gives you a front controller routing to page controllers. You then use the page controllers like the glue to feed stuff into and out of the models, and then into the selected view, before telling the view template to display.

Models will be where the meat of your code is, but a lot of people just make fat page controllers and come back around to making the models do the heavy lifting after they get the project into a phase 2. It's your call. Models really do make your life a whole lot easier, though, when you get going on a huge project. They help you avoid the cut and paste and move into the code reuse. So what you typically do is divide the website project up into what are the major features, and these are called Domain Objects. Then, you have minor features, and those are Sub Objects to the Domain Objects. You can represent that either in one folder or two levels of folders under models. Last, you have the task on a given object, and so that's your actual file. For instance:

```
models/Settings/Employer/Update.php
```

...and inside Update.php you might have a class named like so:

[PHP]class Settings_Employer_Update {
}[/PHP]

So, to load that model, you might create the right system/static_Model.php class such that you can do this:

[PHP]Model::loadModel('Settings/Employer/Update');[/PHP]

Now let's look at the views. You can create XHTML and stick it in your views by creating a folder and file structure under "views" like so:

```
views/Registration/vRegisterForm.php
views/Registration/vRegisterResult.php

```

And inside those files just start with this at the top...

```
<?php ?>
```

and follow with your XHTML. Okay, fine, but how do you get data into those files? Well, a variety of ways, and this is where your system/static_View.php class comes in. You really only have these choices no matter what template engine you use, or if you roll your own:

{VAR} - search and replace tag strategy (slow, even with regexp's or str_replace)
$VAR - pass via global variable strategy (medium fast)
VAR - pass via global constant strategy (super fast)
$SomeObject->VAR -- pass a public var from an object (faster than a global $VAR, but klunky implementation and more typing)

If you use Smarty instead of your own view class, you basically are doing {VAR} but with lots of perks and goodies, should you want those. And you may have heard or used XSLT, and basically it's pretty close to the {VAR} technique as well, although harder and more complex, yet more powerful.

For me, I like using the constants. I like speed. You just have to know the ground rules in PHP about using constants -- they're not like regular variables.

So, for me, my bootstrap.php file loads my View class, and then I would do something like this:

[PHP]View::assignVal('PAGE_TITLE','Registration');
View::displayView('Registration/RegisterForm');[/PHP]

Here you can see that assignVal() basically translates into the PHP define() statement to define a constant. And then displayView basically converts the incoming path to...

```
views/Registration/vRegisterForm.php
```

...and uses require_once() to load it. And because define() creates a global constant, it's immediately available in the file called by require_once().

Next we have the typical DB class for your project. I stick this under the system folder. All I had to do was make the class extend the PDO class that comes with PHP5. Then I start adding in extra goodies I might want, like a routine that gives me an [ActiveRecord]("http://en.wikipedia.org/wiki/Active_record_pattern") class for a quick and dirty ORM. I apply the KISS and obvious principles here -- not too many class methods so that things are crazy, but some of the more obvious ones people would actually want to use repeatedly on projects.

And then anything else you want to add as far as goodies to your framework can be inside the "system" folder. So, for instance, a Dates class, a PDF class, a Timer class, a Cart class, an XML class -- the world is your oyster. Just note, however, that site-specific stuff, not framework-specific stuff, should go into anything but the "system" folder. And framework-specific stuff should go into the "system" folder.

So if anyone complains to you on why you did this versus using ZendFramework, CodeIgniter, whatever -- just say that you can do it better than that, and yet have something that's completely obvious for newbies to get started and using. If someone understands MVC, then they'll easily recognize your framework and learn it fast.

As for why would you want to write your own? Well, why do you think the guys who made CodeIgniter, CakePHP, ZendFramework, Kohana, Symfony -- why do you think those and more decided to write their own framework? It's because it was a reaction to either another framework or because they thought they could do something better and cleaner. Often when I read about PHP frameworks, I keep hearing about scary stuff that people say, such as, "Why the heck does CI do x and y? That's scary! That means problems 1, 2, and 3." and the same for another framework. For me, I like to borrow concepts and ideas from multiple frameworks and do things the most efficient way that I can, minus the bugs and gotchas from other frameworks. I also like the freedom.

But even with all this convincing I'm trying to do here, you will always have guys who will hate you for making your own framework, even if you're completely logical and obvious -- and you'll just have to work with them somehow. If that means learning ZF or CI because that's what people are using on a job site, then you just might have to do it. But isn't it more fun to build your own and convince others that you've built something really, really cool? And I tell you -- build your own MVC framework and you will be able to appreciate every other framework out there, and also learn the skills to help you get started with many frameworks fast, and also learn how to criticize these frameworks. So, by all means, make your own MVC framework and learn this skill.

---

### Post by baustiech on 2009-12-23
Neat and nice article, but despite claiming to be all about speed, it completely negates speed by proposing the use of require_once().

Look into PHP's __autoload() magic function and also, more importantly (when supporting multiple auto_load stacks), spl_autoload_register() instead, for a MUCH faster implementation, everywhere, all the time, easily, and with any existing or new code in PHP 5.3+.

IMHO, anyone still using require_once() for anything, any time, anywhere, in any code base, on anything less than 5.3+, is out of touch and probably isn't getting full speed and serious performance.  NJMHO

[http://php.net/manual/en/language.oop5.autoload.php](http://php.net/manual/en/language.oop5.autoload.php)
[http://www.devshed.com/c/a/PHP/Auto-Loading-Classes-in-PHP-5/](http://www.devshed.com/c/a/PHP/Auto-Loading-Classes-in-PHP-5/)
[http://www.phpro.org/tutorials/SPL-Autoload.html](http://www.phpro.org/tutorials/SPL-Autoload.html)

---

### Post by v8YKxgHe on 2009-12-23
> IMHO, anyone still using require_once() for anything, any time, anywhere, in any code base, on anything less than 5.3+, is out of touch and probably isn't getting full speed and serious performance. NJMHO

Eh, there are plenty of times when require_once() or include_once() are needed. Sure, they are a little slower due to the additional checks, but the speed difference is nothing - and of course you should use include/require for all other situations.

---

### Post by SuperMike on 2009-12-26
Here's my latest PDO wrapper. It's short and simple. If you already know the PDO API, it adds just 3 very useful functions (class methods, actually) on top of that: convertRows(), createInsert(), and createUpdate(). Originally I had this huge PDO wrapper that was complex to remember if I hadn't used it in awhile, and it did way too much in my opinion that I felt my models could do and could have more flexibility. So, I decided to thin it down to something useful, but barebones. That's why I settled on those 3 class methods above.

The "xxx_" prefix is just a unique prefix for my framework. The point is that you can replace it with your own framework prefix.

Your bootstrap in your framework loads the initDB(), and note the xxx_Settings calls my settings class with constants inside, but you can replace that with your own DSN, USER, and PASS vars.

Then, every time you want the established $PDO object in your code, you do a piece of code like:

$PDO = xxx_PDO::getDB();

You can then treat it just like you would a normal PDO library object, or can take advantage of the 3 useful class methods.

Examples:

[PHP]$PDO = xxx_PDO::getDB();
$rsNames = $PDO->query('SELECT * FROM names');
$rsNames = $PDO->convertRows($rsNames);

foreach($rsNames as $rwName) {
  $oName = (object) $rwName;
  print_r($oName);
  echo "<br />\n";
}[/PHP]

[PHP]$PDO = xxx_PDO::getDB();
$oRec = (object) array();
$oRec->FirstName = 'Test';
$oRec->LastName = 'User';
$oRec->Table = 'names';
$st = $PDO->createInsert($oRec);
$st->execute();[/PHP]

[PHP]
$PDO = xxx_PDO::getDB();
$oRec = (object) array();
$oRec->FirstName = 'Test1';
$oRec->LastName = 'User';
$oRec->Table = 'names';
$oRec->Where = "firstname = 'Test'";
$st = $PDO->createUpdate($oRec);
$st->execute();[/PHP]

[PHP]<?php

class xxx_DBO extends PDO {

  // Converts database table column name style into object property naming style,
  // given a PDO recordset.
  public function convertRows(&$rsRows) {
    $asRows = array();
    foreach ($rsRows as $rwRow) {
      $asRow = array();
      foreach ($rwRow as $sOldKey => $vVal) {
        if (intval($sOldKey) === $sOldKey) {
          continue;
        }
        $sNewKey = self::_getObjectKeyName($sOldKey);
        $asRow[$sNewKey] = $vVal;
      }
      array_push($asRows, $asRow);
      $asRow = '';
    }
    return $asRows;
  }

  // Converts a "(object) array()" record object into a PDO Statement object,
  // in this case for UPDATE statements. Also translates object property naming
  // into typical db field naming.
  public function createUpdate($oRec) {
    if (isset($oRec->Table)) {
      $sTable = $oRec->Table;
    }
    if (isset($oRec->Where)) {
      $sWhere = $oRec->Where;
    }
    unset($oRec->Table);
    unset($oRec->Where);    
    if ((empty($sTable)) or (empty($sWhere))) {
      die('<strong>Missing either Table or Where properties on createUpdate.</strong>');
    }
    $s = '';
    foreach ($oRec as $sKey => $sVal) {
      $sKey = self::_getDBKeyName($sKey);
      $s .= $sKey . '=:' . $sKey . ',';
    }
    $s = substr($s, 0, -1);
    $sTable = str_replace('--','',$sTable);
    $sTable = str_replace(';','',$sTable);
    $sWhere = str_replace('--','',$sWhere);
    $sSQL = "
    UPDATE
      $sTable
    SET
      $s
    WHERE
      $sWhere;
    ";
    $PDO = xxx_PDO::getDB();
    $st = $PDO->prepare($sSQL);
    foreach ($oRec as $sKey => $sVal) {
      $sKey = self::_getDBKeyName($sKey);
      $st->bindValue(':' . $sKey, $sVal);
    }
    return $st;  
  }

  // Converts a "(object) array()" record object into a PDO Statement object,
  // in this case for INSERT statements. Also translates object property naming
  // into typical db field naming.
  public function createInsert($oRec) {
    $sTable = $oRec->Table;
    unset($oRec->Table);
    if (empty($sTable)) {
      die('<strong>Missing Table properties on createInsert.</strong>');
    }
    $s1 = ''; $s2 = '';
    foreach ($oRec as $sKey => $sVal) {
      $sKey = self::_getDBKeyName($sKey);
      $s1 .= '' . $sKey . ',';
      $s2 .= ':' . $sKey . ',';
    }
    $s1 = substr($s1, 0, -1);
    $s2 = substr($s2, 0, -1);
    $sTable = str_replace('--','',$sTable);
    $sTable = str_replace(';','',$sTable);
    $sSQL = "
    INSERT INTO $sTable (
      $s1
    ) VALUES (
      $s2
    );
    ";
    $PDO = xxx_PDO::getDB();
    $st = $PDO->prepare($sSQL);
    foreach ($oRec as $sKey => $sVal) {
      $sKey = self::_getDBKeyName($sKey);
      $st->bindValue(':' . $sKey, $sVal);
    }
    return $st;    
  }

  // Converts my typical database table field naming style with an object property naming style.
  private static function _getObjectKeyName(&$sKey) {
    $sKey = strtolower($sKey);
    $sKey = str_replace('fkey_','fk_',$sKey);
    $sKey = str_replace('dt_','Date_',$sKey);
    $sKey = str_replace('_',' ',$sKey);
    $sKey = ucwords($sKey);
    $sKey = str_replace('Ip ','IP ',$sKey);
    $sKey = str_replace(' Ip',' IP',$sKey);
    $sKey = str_replace('Url ','URL ',$sKey);
    $sKey = str_replace(' Url',' URL',$sKey);  
    $sKey = str_replace('name','Name',$sKey); //not a bug -- I conjoin name usually
    $sKey = str_replace(' Id',' ID',$sKey);
    $sKey = str_replace('Id ','ID ',$sKey);
    $sKey = str_replace(' ','',$sKey);
    $sKey = ($sKey == 'Id') ? 'ID' : $sKey;
    $sKey = ($sKey == 'Ip') ? 'IP' : $sKey;  
    $sKey = ($sKey == 'Url') ? 'URL' : $sKey;
    $sKey = str_replace('Fk','FK',$sKey);
    $sKey = ($sKey == 'UserName') ? 'Username' : $sKey;
    return $sKey;
  }

  // Converts my typical object property naming style with a database table field naming style.
  private static function _getDBKeyName(&$sKey) {
    foreach (range('A','Z') as $c) {
      $sKey = str_replace($c, "_$c",$sKey);
    }
    $sKey = str_replace('_F_K_','_fkey_',$sKey);
    $sKey = str_replace('_I_D_','_id_',$sKey);
    $sKey = str_replace('_I_D','_id',$sKey);
    $sKey = str_replace('_I_P_','_ip_',$sKey);
    $sKey = str_replace('_I_P','_ip',$sKey);
    $sKey = str_replace('_U_R_L_','_url_',$sKey);
    $sKey = str_replace('_U_R_L','_url',$sKey);  
    $sKey = str_replace('_Name','name',$sKey); //not a bug -- I separate name usually
    $sKey = str_replace('_Date_','_dt_',$sKey);
    $sKey = str_replace('_Date','_Date',$sKey);
    if (strpos($sKey, '_') == 0) {
      $sKey = substr($sKey, 1);
    }
    $sLast = substr($sKey, -1);
    if ($sLast == '_') {
      $sKey = strrev($sKey);
      if (strpos($sKey, '_') == 0) {
        $sKey = substr($sKey, 1);
      }
      $sKey = strrev($sKey);
    }
    $sKey = strtolower($sKey);
    return $sKey;
  }

}


class xxx_PDO {

    private static $_hInstance;
    private $_hDB;
    
    private static function _get_ANSI_SQLSTATE_Code(&$e) {
    $s = $e->__toString();
    $asItems = explode('[', $s);
    $s = $asItems[1];
    $asItems = explode(']', $s);
    $s = $asItems[0];
    return trim($s);
  }
  
  public static function initDB() { // call this by bootstrap
  
    $oDB = self::_getInstance();
    try {
      $oConn = new xxx_DBO(xxx_Settings::get('DSN'), xxx_Settings::get('DSN_USER'), xxx_Settings::get('DSN_PASS'));
    } catch (PDOException $e) {
      $SQLSTATE = self::_get_ANSI_SQLSTATE_Code($e);
      switch ($SQLSTATE) {
        case 28000:
          $sErr = 'The database user is not created or the password is wrong for database user: ' . xxx_Settings::get('DSN_USER');
          break;
        default:
          echo 'SQL ERROR: ';  
          print_r($e->getCode());
          die();      
      }
      die('<strong>' . $sErr . '</strong>');
    }
    $sTest = xxx_Settings::get('DSN');
    if (strpos(' ' . $sTest, 'mysql:')>0) {
      $oConn->setAttribute(PDO::MYSQL_ATTR_MAX_BUFFER_SIZE, 1024*1024*50);
    }
    unset($sTest);
    $oConn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
    $oConn->setAttribute(PDO::ATTR_PERSISTENT,TRUE);
    $oConn->setAttribute(PDO::ATTR_CURSOR, PDO::CURSOR_FWDONLY);
    
    $oDB->_hDB = $oConn;
  }
    
  public static function getDB() { // call this to get last established database connection handle
    $oDB = self::_getInstance();
    return $oDB->_hDB;
  }
    
  private static function _getInstance() {
    if (self::$_hInstance == null) {
      $sClassName = __CLASS__;
      self::$_hInstance = new $sClassName();
    }
    return self::$_hInstance;
  } 

} //end xxx_PDO
[/PHP]

---

### Post by SuperMike on 2009-12-26
> **baustiech said:**
> Neat and nice article, but despite claiming to be all about speed, it completely negates speed by proposing the use of require_once().

Look into PHP's __autoload() magic function and also, more importantly (when supporting multiple auto_load stacks), spl_autoload_register() instead, for a MUCH faster implementation, everywhere, all the time, easily, and with any existing or new code in PHP 5.3+.

IMHO, anyone still using require_once() for anything, any time, anywhere, in any code base, on anything less than 5.3+, is out of touch and probably isn't getting full speed and serious performance.  NJMHO

[http://php.net/manual/en/language.oop5.autoload.php](http://php.net/manual/en/language.oop5.autoload.php)
[http://www.devshed.com/c/a/PHP/Auto-Loading-Classes-in-PHP-5/](http://www.devshed.com/c/a/PHP/Auto-Loading-Classes-in-PHP-5/)
[http://www.phpro.org/tutorials/SPL-Autoload.html](http://www.phpro.org/tutorials/SPL-Autoload.html)

Thanks, for this! :)

I'll have to check how far back this __autoload() and/or other loading mechanisms work because I want to use my framework on any PHP5 installation. There's still a lot of 5.2 out there, unfortunately.

Also, my framework uses include(), but I do a file_exists() check first. Perhaps this is slower? If anyone knows, let me know.

---

### Post by Hellkeepa on 2009-12-26
HELLo!

"__autoload()" is available on all PHP 5.x installations, as noted in the manual.
> As of PHP 5...

As for "include()" vs "file_exists(); include()", of course the latter is slower; It does more. However, unless you're including a *lot* of files this performance hit is neglible. Especially so if you use it for error handling. If you do inlcude so many files that his becomes an issue, then your problem is something else entierly, namely the structure of your system.

Happy codin'!

---

