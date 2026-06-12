---
title: "Php - Recaptcha"
date: 2008-06-16
forum: Programming Talk
---

### Post by Tux.Ice on 2008-06-16
ok UPDATE:
i am trying to set it so that when recaptcha is valid it sets $recaptcha to "1" but if it is invalid sets it to "0". heres my recaptcha code:
it also wont allow the fopen without $recaptcha being "1"
```
<?php

require_once('recaptchalib.php');

// Get a key from http://recaptcha.net/api/getkey
$publickey = "6LdLMgIAAAAAADm2aLW7b8c6wo1OGRdyaGxg1xGN ";
$privatekey = "6LdLMgIAAAAAALEw_CSkv4BLdYCLUgpnkLLrkAnP ";

# the response from reCAPTCHA
$resp = null;
# the error code from reCAPTCHA, if any
$error = null;

# was there a reCAPTCHA response?
if ($_POST["recaptcha_response_field"]) {
        $resp = recaptcha_check_answer ($privatekey,
                                        $_SERVER["REMOTE_ADDR"],
                                        $_POST["recaptcha_challenge_field"],
                                        $_POST["recaptcha_response_field"]);

        if ($resp->is_valid) {
                echo "You got it!";
        } else {
                # set the error code so that we can display it
                $error = $resp->error;
        }
}
echo recaptcha_get_html($publickey, $error);
?>
```

the form which submits this information along with the username & password, etc is called submit.php and it is this ```
<?php


# You can pass following parameters in calling URL. They will
# override those specified below.
# user - new email user
# pass - password
# domain - email domain
# quota - email quota, Mb
# Example: cpemail.php?user=newuser&pass=password&quota=50



$cpuser = 'techo'; // cPanel username
$cppass = 'MYCPANELPASS'; // cPanel password
$cpdomain = 'techotech.com'; // cPanel domain or IP
$cpskin = 'x';  // cPanel skin. Mostly x or x2. 


// Default email info for new email accounts
// These will only be used if not passed via URL
$edomain = 'techotech.com'; // email domain (usually same as cPanel domain above)
$equota = 512; // amount of space in megabytes



function getVar($name, $def = '') {
  if (isset($_REQUEST[$name]))
    return $_REQUEST[$name];
  else 
    return $def;
}

// check if overrides passed
$euser = getVar('user', '');
$epass = getVar('pass', $epass);
$edomain = getVar('domain', $edomain);
$equota = getVar('quota', $equota);
$recaptcha = getVar('recaptcha', $recaptcha);

$msg = '';
if ($recaptcha == "0")
while(true) {

  

  // Create email account
  $f = fopen ("http://$cpuser:$cppass@$cpdomain:2082/frontend/$cpskin/mail/doaddpop.html?email=$euser&domain=$edomain&password=$epass&quota=$equota", "r");
  if (!$f) {
    $msg = 'Cannot create email account. Error Code: 0xPHPSAFE98';
    break;
  }

  $msg = "<h2>Email account {$euser}@{$edomain} successfully created.</h2>";

  // Check result
  while (!feof ($f)) {
    $line = fgets ($f, 1024);
    if (ereg ("already exists", $line, $out)) {
      $msg = "<h2>Email account {$euser}@{$edomain} already exists.</h2>";
      break;
    }
  }
  @fclose($f);

  break;

}

?>

<?php echo '<div style="color:blue">'.$msg.'</div>'; ?>
```

---

### Post by Tux.Ice on 2008-06-17
bump

---

### Post by MacAnthony on 2008-06-17
Maybe I'm reading this wrong but wouldn't you just change:

```

        if ($resp->is_valid) {
                echo "You got it!";
        } else {
                # set the error code so that we can display it
                $error = $resp->error;
        }

```

To:
```

        if ($resp->is_valid) {
                $recaptcha = 1; // or true
                echo "You got it!";
        } else {
                $recaptcha = 0; // or false
                # set the error code so that we can display it
                $error = $resp->error;
        }

```

Am I missing something?

---

### Post by Tux.Ice on 2008-06-17
oh yes that would set the variable $recaptcha to 1 but i need to know how to make it check (in submit.php) if $recaptcha is 1 before displaying a messige or fopening the link.

---

### Post by MacAnthony on 2008-06-17
I don't understand the relationship between code sample 1 and code sample 2. If CS1 is included in CS2, then the checking that is being done in CS2 is fine. If they are directed to CS1 and then redirected back to CS2, then you would have to save the value some where like in a session variable or pass it on the getline (not recommended since the user can change it).

---

### Post by Tux.Ice on 2008-06-17
CS1 passes variables on to CS2 through the getline (i know its insecure) but how would you do this, validating the recaptcha?

---

### Post by MacAnthony on 2008-06-18
You should just be able to check the value then:

```

if ( isset($_GET['recaptcha']) && $_GET['recaptcha'] == '1' )
{
    // do stuff
}

```

In the CS2 file.

---

