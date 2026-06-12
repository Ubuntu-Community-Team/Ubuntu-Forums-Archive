---
title: "PHP error, trying to center index.php"
date: 2007-10-05
forum: Programming Talk
---

### Post by American_Outcast on 2007-10-05
I can edit and play around with PHP, but my knowledge is limited. So please be nice, lol.

I was going to search for the problem but I am not really sure where to start. I am using a content management system, mysql and a template for the content management system. I can add HTML code before <?php and after ?> as long as it has the opening and closing tags, ex. <html><body></body></html>

The content management system has everything aligned to the left. I want it centered. So I have been trying this.

<center> 
<?php  
PHP code
?>
</center>

<div align="center">
<?php
PHP code
?>
</div>

I even tried "wrapping" it with html code before <?php and after ?> and I still get these errors. (pasted at the end of this post.) Also I don't get these errors if I leave it as it was.

Anyone know how I can center this without errors?

Thanks in advance



Warning: session_start() [function.session-start]: Cannot send session cookie - headers already sent by (output started at /home/homes/public_html/real/index.php:2) in /home/homes/public_html/real/index.php on line 34

Warning: session_start() [function.session-start]: Cannot send session cache limiter - headers already sent (output started at /home/homes/public_html/real/index.php:2) in /home/homes/public_html/real/index.php on line 34

Warning: Cannot modify header information - headers already sent by (output started at /home/homes/public_html/real/index.php:2) in /home/homes/public_html/real/index.php on line 35

---

### Post by bobbocanfly on 2007-10-05
Those errors have nothing to do with centering. The first 2 are about setting cookies and the last im guessing is about redirecting a user.

---

### Post by American_Outcast on 2007-10-05
This is strange then. I only get those errors when I add, for ex. <center> before <?php and  </center> after ?> 

Maybe adding tags like that is interfering with parts of the php code in between "<?php ?>"?

---

### Post by American_Outcast on 2007-10-05
It would probably be helpful if I post the index.php code I currently have that is producing the errors,


> <html><body> <center>
<?php
@ini_set('arg_separator.output', '&amp;');
@ini_set('url_rewriter.tags', 'a=href,area=href,frame=src,input=src');

session_start();
header("Cache-control: private"); 

$filename = dirname(__FILE__) . '/install/index.php';
if (file_exists($filename)) {
	die ('<html><div style="color:red;text-align:center">You must delete the file ' . $filename . ' before you can access your install.</div></html>');
}

if (isset($_POST['select_users_lang'])) {
	session_register('users_lang');
	$_SESSION['users_lang'] = $_POST['select_users_lang'];
}

global $config, $conn, $css_file;
$css_file = '';
require_once(dirname(__FILE__) . '/include/common.php');

$pos = strpos($config['admin_email'], 'ty.org');
$pos2 = strpos($config['admin_email'], 'changeme@default.com');
if ($pos !== false || $pos2 !== false) {
	die ('<html><div style="color:red;text-align:center">You must set an administrative email address in the site configuration before you can use your site. </div></html>');
}

require_once($config['basepath'] . '/include/misc.inc.php');
$misc = new misc();
$start_time = $misc->getmicrotime();

ob_start();
if (!isset($_GET['printer_friendly'])) {
	$_GET['printer_friendly'] = false;
}

if (isset($_SESSION["users_lang"]) && $_SESSION["users_lang"] != $config['lang']) {
	include($config['basepath'] . '/include/language/' . $_SESSION['users_lang'] . '/lang.inc.php');
}else {

	unset($_SESSION["users_lang"]);
	include($config['basepath'] . '/include/language/' . $config['lang'] . '/lang.inc.php');
}

if (isset($_GET['action']) && $_GET['action'] == 'logout') {
	require_once($config['basepath'] . '/include/login.inc.php');
	$login = new login();
	$login->log_out('user');
}elseif (!isset($_GET['action'])) {
	$_GET['action'] = 'index';
}
require_once($config['basepath'] . '/include/class/template/core.inc.php');
		$page = new page_user;
if(strpos($_GET['action'],'rss_') !== 0){
	if (isset($_GET['popup'])) {
		$page->load_page($config['template_path'] . '/popup.html');
		}elseif (isset($_GET['printer_friendly']) && $_GET['printer_friendly'] == 'yes') {
		$page->load_page($config['template_path'] . '/printer_friendly.html');
		}else {
		if (isset($_GET['PageID']) && file_exists($config['template_path'] . '/page' . $_GET['PageID'] . '_main.html')) {
			$page->load_page($config['template_path'] . '/page' . $_GET['PageID'] . '_main.html');
		}elseif ($_GET['action'] == 'index' && file_exists($config['template_path'] . '/page1_main.html')) {
			$page->load_page($config['template_path'] . '/page1_main.html');
		}else {
			$page->load_page($config['template_path'] . '/main.html');
		}
	}
}else{
	$page->page='{content}';
}

global $jscript,$jscript_last;
$jscript = '';
$jscript_last = '';

$page->replace_tags(array('content'));

$page->replace_permission_tags();
$page->replace_urls();
$page->auto_replace_tags();

$page->replace_tags(array('load_js','load_js_last'));

$page->replace_lang_template_tags();
$page->replace_css_template_tags();
$page->replace_meta_template_tags();
$page->output_page();
$conn->Close();

$buffer = ob_get_contents();
ob_end_clean();
echo $buffer;

$end_time = $misc->getmicrotime();
$render_time = sprintf('%.3f', $end_time - $start_time);
echo '<!-- This page was generated in ' . $render_time . ' seconds -->';

?>

</center></body></html>

---

### Post by keithweddell on 2007-10-06
The answer to your problem is output buffering see [this link]("http://www.php.net/manual/en/ref.outcontrol.php") to the PHP Manual.  The errors are complaining that your HTML has already been sent to the browser before the php code tries to amend the output.  When using php, you have to send all output to the browser in a single burst.  I'm sure you can find better explanations by googling "php output buffer" or something similar.

Keith

---

### Post by SreckoMicic on 2007-10-06
^^ As sad above, just try not to send to browser nothing (mean nothing) before sending headers.

---

### Post by bobbocanfly on 2007-10-06
If that doesnt work (guessing it will but just in case) you could try echo'ing your center tag like

```
echo '<center>';
```

---

### Post by keithweddell on 2007-10-06
Actually, looking closer at your code, output buffering is started around line 34: ```
ob_start();
```
and closed about 10 lines from the end:
```
$buffer = ob_get_contents();
ob_end_clean(); 
```

If you put your starting html and closing html between these lines (using echo as suggested above) it should work.

Keith

---

### Post by American_Outcast on 2007-10-06
Thank you both very much.  I cant check this at the moment but when I get back in a few hours I will give this a try.

---

### Post by American_Outcast on 2007-10-09
Below is what the two lines of code where and what I changed them to to get the results I needed. Now everything works fine. But, can someone please tell me the importance of these two lines with Internet Explorer? Or what they are suppose to do? It appears to work with IE6, but they are there for some reason. Also can I put this code somewhere else maybe, so it works well. Or is there something else I can use in its place?

Thanks in advance.

I have <center> Before <?php and </center> after ?>

(WAS, when I got the errors I posted earlier in this thread.)
session_start();
header("Cache-control: private"); //IE6 Form Refresh Fix

(NOW, and it centers it fine without the errors mentioned earlier.)
//session_start();
//header("Cache-control: private"); //IE6 Form Refresh Fix

---

### Post by American_Outcast on 2007-10-10
Anyone?

I did find out this has to do, I think, with hitting the back button in Internet Explorer. My searching found this but I am not sure if this is the right fix for it.

> <?php
header("Expires: Mon, 26 Jul 1997 05:00:00 GMT");
header("Last-Modified: " . gmdate("D, d M Y H:i:s") . " GMT");
header("Cache-Control: no-store, no-cache, must-revalidate");
header("Cache-Control: post-check=0, pre-check=0&#8243;, false);
session_start();
header("Cache-Control: private");
?>

---

### Post by #Reistlehr- on 2007-10-10
Just for your reference.

The error is produced when you have a session start, or anything referencing a header with code that is echo'd, printed, or exist before they are read.

So you can do,

<?php
session();
echo "i started a session";
?>

but NOT
<?php
echo "i started a session";
session();
?>

It's much like PEMDAS in math, the order of operations. Parenthensis before exponents, then multiply and divide, then add and subtract.

---

### Post by American_Outcast on 2007-10-10
> **#Reistlehr- said:**
> Just for your reference.

The error is produced when you have a session start, or anything referencing a header with code that is echo'd, printed, or exist before they are read.

So you can do,

<?php
session();
echo "i started a session";
?>

but NOT
<?php
echo "i started a session";
session();
?>

It's much like PEMDAS in math, the order of operations. Parenthensis before exponents, then multiply and divide, then add and subtract.

Thanks.

Due to the errors I am getting I am going to start over and just work on a different CMS. I will work on this CMS in the near future after I learn a little more about php.

---

