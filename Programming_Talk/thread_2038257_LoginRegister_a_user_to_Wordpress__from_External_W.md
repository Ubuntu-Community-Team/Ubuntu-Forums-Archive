---
title: "Login/Register a user to Wordpress  from External Website"
date: 2012-08-06
forum: Programming Talk
---

### Post by ivikas on 2012-08-06
[PHP]<?php ob_start();

require($_SERVER['DOCUMENT_ROOT']."/index.php"); /* Include wordpress main index file,we get access to "all wp-function(not tested)" in our external file.*/

define('WP_USE_THEMES', false); // Do not show themes

header("HTTP/1.1 200 OK"); /* Sometimes error occurs,so to fix we set headers */


$email = 'someuser@somewhere.com'; /* Get username or password from form */
	
if (!email_exists($email))
{
 echo 'That E-mail doesn\'t belong to any registered users on   this site,So registering....<br>';

// Creating WP User
wp_create_user( 'someuser', 'passme', 'someuser@somewhere.com'); 
echo 'This email id is now registered thanks--->'.$email;
    	
}
else
{
 echo "That E-mail id is already registered !! So, automatically signing in...";    	

	$creds = array();
	$creds['user_login'] = 'someuser';
	$creds['user_password'] = 'passme';
	$creds['remember'] = true;

        // Sigining in a WP User
	$user = wp_signon( $creds, false ); 

	if( is_wp_error($user))
	{

	  echo 'oops!! we got some error in sigining in '.$user->get_error_message();

	}
	else
	{
 	  echo '<br>User is now logged in !!<br>';
   }		
}
ob_end_flush();
?>[/PHP]

---

