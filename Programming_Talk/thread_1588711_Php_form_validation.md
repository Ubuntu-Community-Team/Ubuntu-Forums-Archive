---
title: "Php form validation"
date: 2010-10-05
forum: Programming Talk
---

### Post by Sugz on 2010-10-05
Hello, 

IM getting to grips with Php having come from a Java, JSP and JSF background, 

I am currently doing a form (as a test) and I want to pass the form values to an external Php Script, and the result of the Form (the value of a variable) determines weather the form has been validated, 

however what I am wanting to know, its how do I access the variable set by the script so I can output the appropriate HTML to tell the user that that there is an error with the form - I am wanting to keep the Scripting and the HTML seperate, so as to keep my HTML as clean and readable as possible. 

So to put simply. 

1 - User fills in form
2 - Form contents are sent to the external script
3 - There is a problem - return to the previous page (or refresh) with an error message in the form of HTML) - whos value is determined by a Variables contents in the script. 

or

4 - The form is OK - return to the page with a conformation message!


All the examples I have seen, use Inline PHP (php embedded in the HTML) But I consider this messy and counter productive. 

Any help would be greatly appreciated
- Sugz

---

### Post by soapytheclown on 2010-10-05
id say use an mcv framework to seperate your logic and presentation if you dont like the idea of mixing the html and php so much. i use the zend framework but its got a fairly steep learning curve. You should post up some code so we can see what you've done so far :)

---

### Post by Sugz on 2010-10-05
I mean to get going with an MVC-based framework, but my time and knowledge is such that Im trying to keep my Php as simple as possible at the moment :P

So far, I have fully coded both the Php Page with the form on, and script which it referenced. 

I have posted only the parts that matter as I dont particularly want to post everything. 

```
.
.
.
.
.
<form  method="POST" action="contacthandler.php">  
                <label> 
                  <span> Your Name * </span> 
                  <input type="text" class="input_text" name="name" id="name" />
                </label>
                
                <label> 
                  <span> Your E-mail </span> 
                  <input type="text" class="input_text" name="company" id="company" />
                </label>
                
                <label> 
                  <span> Your company </span> 
                  <input type="text" class="input_text" name="email" id="email" />
                </label>
                
                <label> 
                  <span> Your Message * </span> 
                  <textarea class="message" name="message" id="message"></textarea>
                </label>
                <input type="submit" class="button" value="SEND" name="send"/> </input>
                <div class="clear" style="clear:both;"> </div> 
           </form>
           
           
    </div>
    
        <?php
           if($_POST && isset($missing) && !empty($missing)){
           ?>
           <p class="norm"> Please complete the missing Item(s) indicated </p>
           <?php } ?>
            <?php if($_POST && !$mailSent){
            ?>
            <p class="norm"> Form not submitted! doh! </p>
            <?php
                } else if($_POST && $mailSent){
                ?>
                <p class="norm"> Form Sent! Woohoo! </p>
                <?php 
                    } ?>
    
  </div>  
```

The Script

```
<?php
if(array_key_exists('send', $_POST)){
        $to = "###.###@######.co.uk";
        $c_subject = "#### Contact reply";
        
        $expected = array('name', 'email', 'company', 'message');
        $required = array('name', 'message');
        $missing = array();
        
        foreach($_POST as $key => $value){
            $temp = is_array($value) ? $value : trim($value);
                if(empty($temp) && in_array($key, $required)){
                    array_push($missing, $key);
                }
                elseif(in_array($key, $expected)){
                ${$key} = $temp;
                }
        }
        
        if(empty($missing)){
        
        $c_body = "FROM: $name \n COMPANY: $company \n EMAIL: $email \n MESSAGE: $message";
        $c_body = wordwrap($c_body, 100);
        $mailSent = mail($to, $c_subject, $c_body);
        if($mailsent){
        unset($missing);
        }
        $page = "Contact.php";
        $sec = "0.5";
        header("Refresh: $sec; url=$page");
    else{
    $page = "Contact.php";
    $sec = "0.5";
    header("Refresh: $sec; url=$page");
    }
    }
    }
    
?>
```

Basically, I want the value of $missing (if it is not empty) to output a different line of HTML (as seen in the first Block of code) 

But I cannot get the php page and the Script to talk to eachother (It works fine if All the required fields are not empty) so that If something has gone wrong, then the user is sent back to the Form page with an error message attached.

---

### Post by spjackson on 2010-10-05
I'm only a novice with php, but I'll have a go.

I know of at least two possibilities: pass data in the URL, or use a php session.

For the first method, you would put, say

```

$page = "Contact.php?missing=email";

```then in your Contact.php page you'd have, say
```

if (isset($_GET['missing']) && $_GET['missing'] !="") { 
   /* do stuff */
}

```Drawbacks are that you need to format your data as a valid URL and that format gets shown to the user.

For the php session method, here's a tutorial [http://www.tizag.com/phpT/phpsessions.php](http://www.tizag.com/phpT/phpsessions.php)

I hope that helps.

---

### Post by soapytheclown on 2010-10-06
i actually wrote something like this for a friend the other day its a bit more complicated than what you've been working with atm but does everything you're looking for and its not too difficult to understand (i dont think so anyway) here it is:

contact.php
[PHP]
<?php
require('components/Email.php');
$mail = new Email();

if(isset($_POST) && isset($_POST['name']) &&   isset($_POST['email']) && isset($_POST['subject']) && isset($_POST['message']) ){
    
    if( $mail->Email($_POST['email'], $_POST['name'], $_POST['subject'], $_POST['message']) ){
        echo "<p class='success'>Message Sent</p>";
    }else{
        $errors = $mail->GetErrors();
        echo "<p class='error'>";
        foreach($errors as $e){
            echo $e.'<br/>';
        }
        echo "</p>";
    }
}
?>

<form action="/contact.php" method="post" id="frmContact">

    <dl>
        <dt><label for="name">Name</label></dt>
        <dd>
            <input tabindex="1" type="text" name="name" id="name"
               value="<?php if(isset($_POST['name']) && isset($errors) && is_array($errors)) echo $_POST['name'];?>" />
        </dd>

        <dt><label for="email">Email Address</label></dt>
        <dd>
            <input tabindex="2" type="text" name="email" id="email"
               value="<?php if(isset($_POST['email']) && isset($errors) && is_array($errors)) echo $_POST['email'];?>"/>
        </dd>

        <dt><label for="subject">Subject</label></dt>
        <dd>
            <input tabindex="3" type="text" name="subject" id="subject"
               value="<?php if(isset($_POST['subject']) && isset($errors) && is_array($errors)) echo $_POST['subject'];?>"/>
        </dd>

        <dt><label for="message">Message</label></dt>
        <dd>
            <textarea tabindex="4" name="message" id="message" rows="5" cols="40"><?php if(isset($_POST['message']) && isset($errors) && is_array($errors)) echo $_POST['message'];?></textarea>
        </dd>

        <input tabindex="5" type="submit" value="Send" id="submit"/>
    </dl>

</form>

[/PHP]

components/Email.php
[PHP]
/**
 * Description of Email
 *
 * @author talv
 * @email talvbansal [at] gmail [dot] com
 */
require_once('Email/EmailInterface.php');

class Email implements EmailInterface{
    //put your code here

    private $_to;
    private $_headers;
    private $_errors = array();

    public function  __construct() {
        $this->_to = 'email@address.com';

    }

    public function  Email($from, $name, $subject, $message) {

        if( $this->validate($from, $name, $subject, $message) ){

            $this->_headers =
                'From: '.$from. "\r\n" .
                'Reply-To: '.$from."\r\n" .
                'X-Mailer: PHP/' . phpversion();

            if( mail($this->_to, $subject, $message.' from '.$name, $this->_headers) ){
                return true;
            }else{
                $this->_errors[] = 'Unable To Send Message At This Time';
                return false;
            }

        }
        return false;
        

    }

    private function validate(&$from, &$name, &$subject, &$message){

        if( !preg_match('/^[^@]+@[a-zA-Z0-9._-]+\.[a-zA-Z]+$/', $from) ){
            $this->_errors[] = 'Invalid Email Address';
        }

        $this->alpha($name, 'Name');
        $this->alpha($subject, 'Subject');
        $this->alpha($message, 'Message');

        if( empty($this->_errors) ){
            return true;
        }
        return false;
        
    }

    private function alpha($el, $name){
        $pattern  = '/^[a-zA-Z0-9_.-\/-#:,\(\)  ]{1,256}$/D';
        $el = trim($el);
        if(!preg_match($pattern,$el) || empty($el) ){
            $this->_errors[] = ($name." Must Be Contain Alphanumeric Characters Only");
        }
    }

    public function GetErrors(){
        return $this->_errors;
    }

    public function GetEmail(){
        $e = $this->_to;
        $output = NULL;
        for ($i = 0; $i < strlen($e); $i++) { $output .= '&#'.ord($e[$i]).';'; }
        return $output;
}

}
?>
[/PHP]

components/Email/EmailInterface.php
[PHP]
<?php
interface EmailInterface{
    public function Email( $from, $name, $subject, $message );
    public function GetErrors();
    public function GetEmail();
}
?>

[/PHP]


if you need any further help with it feel free to email me :)

---

### Post by Sugz on 2010-10-06
Thats a neat little script you have there, many thanks indeed. 
I wont copy and past obviously, but I will certainly take some pointers from it. :popcorn:

---

### Post by soapytheclown on 2010-10-06
no problem i dont mind if you use it :) like i said if you need any more help or me to explain any of it my email addy is in the script :)

---

