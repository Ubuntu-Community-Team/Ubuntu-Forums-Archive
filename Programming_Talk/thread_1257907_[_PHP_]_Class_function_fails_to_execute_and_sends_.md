---
title: "[ PHP ] Class function fails to execute and sends an &quot;exit&quot; signal."
date: 2009-09-04
forum: Programming Talk
---

### Post by credobyte on 2009-09-04
Ok, let me explain ..
When you open index.php ( main page ), Main class will check for your current location and redirect to where you should be, not where you are now.
Once you are on the right page, it'll include current pages content from another file.

Keep in mind - until now, all operations have been completed successfully.

Now, the problem is that, I can't execute anything related to my class files from my "content" file ( eg., $func->say("hello") ). Obviously, as I've already included all core files in my index.php, I'm not including them again in my content file.

Does anybody see a single reason, why it should fail ? :(

[COLOR=Gray]P.S. - not the best explanation, but .. better than nothing.[/COLOR]
[B]
index.php
[/B][php]<?php include("system/mysql.class.php"); ?>
<?php include("system/main.class.php"); ?>

<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN">
<html>
    <head>
        <meta http-equiv="Content-Type" content="text/html; charset=UTF-8">
        <link href="style.css" rel="stylesheet" type="text/css">
        <title> <?php echo SITE_TITLE; ?> </title>
    </head>
    <body>

        <?php $func->getPageContent(); ?>

    </body>
</html>[/php][B]

exchange.php
[/B][php]<script src="javascript/exchange.js" type="text/javascript"></script>

<div id="status">
    Exchange status ..
</div>

<?php
$func->say("hello");    // nothing happens here
?>[/php][B]

mysql.class.php
[/B][php]<?php

require_once("config.php");

class MySQL {

    protected $db_host = DB_HOST;
    protected $db_user = DB_USER;
    protected $db_pass = DB_PASS;
    protected $db_name = DB_NAME;

    public $connection, $database;

    function __construct()
    {
        $this->connect();
    }

    function connect()
    {
        $this->connection = @mysql_connect($this->db_host, $this->db_user, $this->db_pass) or die($this->error());
        $this->database = @mysql_select_db($this->db_name) or die($this->error());
    }

    function error()
    {
        echo "[MySQL] " . mysql_error();
        exit();
    }

}

$SQL = new MySQL();

?>[/php][B]

main.class.php[/B]
[php]<?php

class Main {

    function __construct()
    {
        $this->getLocation();
    }

    function say($what)
    {
        echo $what;
    }

    function getLocation()
    {
        $page_index = $_GET['location'];
        
        if (!isset($page_index)) {
            $this->redirect("index.php?location=main");
        } else {
            return $page_index;
        }
    }

    function getPageContent()
    {
        $page_index = $_GET['location'];

        if ($page_index == "main") {
            include("content/main.php");
        } else if ($page_index == "exchange") {
            include("content/exchange.php");
        } else {
            echo "Page not found!";
        }
    }

    function redirect($target)
    {
        echo '<script type="text/javascript">';
        echo 'window.location = "' . $target . '";';
        echo '</script>';
    }

}

$func = new Main();

?>[/php]

---

