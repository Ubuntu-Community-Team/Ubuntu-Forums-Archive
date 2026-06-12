---
title: "php oop yeah you know me..."
date: 2010-03-02
forum: Programming Talk
---

### Post by cacycleworks on 2010-03-02
Hi Everyone,

I have set out upon a strange new adventure for me. I am working on abstracting classes to make my (our) code generic, modular, and portable. I have spent a few days scouring php.net and the rest of the intarwebs for help and am stumped.

See, everything I read about classes, extends, etc etc work backwards. Example:

[PHP]class message {
  function send() {
    ;
  }
}

class email extends message{
  function send() {
    // sendmail blah blah
  }
}

$msg=new email;
$msg->send();
[/PHP]

My problem is that the code where $msg is created shouldn't know that it's an email or even have access to that class... So I ended up working my way around and around and came up with this kludgy feeling thing:

[PHP]class message {
  $this->deliveryType="";

  function setEmailDelivery(){
    include_once( "class.email.php" );
    $this->deliveryType=new email($this);
  }

  function send() {
    if( is_object($this->deliveryType) )
      $this->deliveryType->{__FUNCTION__}();
  }


}

class email extends message {
  function send() {
    // sendmail blah blah
  }
}

$msg=new message;
$msg->setEmailDelivery();
$msg->send();
[/PHP]

I believe that someone here HAS to know the better way: would you please point out a reference to this better way?

For the curious, I'm building an information exchange to connect business functions together. Example: to ship packages, the code needs access to the accounting software. But the logic code shouldn't need to know anything about it... so I want to do this:
logic :: accounting :: xTuple or... logic :: accounting :: quickbooks

And the logic also needs to talk to various shipping companies' APIs. We've got the ups XML connector working, so then we need:
logic :: shipping :: ups 

So that inside the logic class, logic says to accounting: give me all orders ready to ship. Then the accounting class asks the product-specific class to do the handshaking to get the data. We are going to gnu license and share our classes once we get our application sorted out. 

Thanks so much in advance!
Chris

---

### Post by CptPicard on 2010-03-02
I'm not quite sure I get your design problem, but I suspect here is a clue:

> **cacycleworks said:**
> 
My problem is that the code where $msg is created shouldn't know that it's an email or even have access to that class...

Have you thought of using some kind of builder/factory method or other kind of factory pattern that is capable of abstracting the exact type of object being created at the point of creation?

(Disclaimer: never done any PHP...)

---

### Post by cacycleworks on 2010-03-02
> **CptPicard said:**
> Have you thought of using some kind of builder/factory method or other kind of factory pattern that is capable of abstracting the exact type of object being created at the point of creation?

(Disclaimer: never done any PHP...)

Hhahaha, love the disclaimer. Yes, I've been reading on those but I haven't figured it out yet ... they don't give examples that actually show what's going on. And once there are about 500 or 1000 words, my eyes glaze over and my brain melts out my ears.

I know I'm on the brink of getting it, too... 

Thanks!
:) Chris

---

### Post by CptPicard on 2010-03-02
> **cacycleworks said:**
> Hhahaha, love the disclaimer.

Well, this seems like an application of a general OOP principle that is pretty language-independent :)

The idea really is that you have a function that you constructs an object for you according to some parameters passed to that function. At the point of call of the function, you don't care which subclass of some base class the returned object exactly is; the information of the exact subclass that was selected for returning is strictly inside the factory function...

---

### Post by Reiger on 2010-03-02
Factory methods typically work like this:

[php]
<?php
class Email implements MyResultType {
   function __construct(/* args*/) {
      // use args as appropriate
   }
   
   function send() {
      // implementation logic here
   }
   /* more methods to manipulate Email */
}

// interface to define factory method return type
interface MyResultType {
   // methods to expose data/functions as required.
}

// interface to define data type
interface MyDataType {
  // methods to expose data/functions as required.
}

// class to hide nitty gritty details of object construction on the higher API level
class MyFactory {
  function getObject($myObject) {
      $myResult= /*
      * code to retrieve data from $myObject via interface methods
      * construct result object of the right type and initialize it as necessary
      
      */;
      return $myResult;
  }
  /* code to get/set factory properties/configuration */
}
[/php]

That can be as simple as (factoring out complexity):

[php]
class TextOutput implements Output {
  function send($msg) {
    header('Content-type: text/plain');
    echo $msg;
  }
}
class HTMLOutput implements Output {
  function send($msg) {
    header('Content-type: text/html');
    echo $msg;
  }
}
class XMLOutput implements Output {
  function send($msg) {
    header('Content-type: application/xml');
    echo $msg;
  }
}

interface Output {
  /** send output to HTTP socket
   *@param $msg content to output
   */
  send($msg);
}

class OutputFactory {
   /* 
    *  static method for convenience,
    *  saves me the code of instantiating an OutputFactory object
    */
   static function getOutput() {
      $type= isset($_GET['type']) ? $_GET['type'] : 'html';
      switch($type) {
        case 'text': return new TextOutput();
        case 'xml' : return new XMLOutput();
        default: return new HTMLOutput();
      }
   }
}

$msg=<<EOT
<html>
  <head><title>Hello world!</title></head>
  <body><h1>Hell world!</h1></body>
</html>
EOT;

OutputFactory::getOutput()->send($msg);
?>
[/php]

---

### Post by cacycleworks on 2010-03-02
Thank you for the clear and intelligent example!! I will play with this and reply. (hopefully with success) 

:) Chris

---

### Post by Simon17 on 2010-03-02
Thread title made me laugh.

(Nice example by the way, Reiger.)

---

### Post by cacycleworks on 2010-03-03
Wow it's been a fun past few days... I kept working with Reiger's sample, then I downloaded PEAR::DB to check it over.

I kept going around and around with this with my goal of complete simplicity. My whole thing with this is the PHP code closest to the actual user interface, shouldn't know anything about inherited classes, methods, factory, etc...

So I'm really going after a super clean API.

I expounded upon my code from before and came up with this:

[PHP]<?
class Ship extends infoX { 
	function __construct() {
		parent::__construct();
		$this->carrierClassName="Ups";
		$this->accountingClassName="xTuple";
		
		$this->set_carrier();
		$this->set_accounting();
	} // construct
	
	function set_carrier( $class="" ){
		if( strlen( $class ) > 2 )
			$this->carrierClassName=$class;
		$this->carrier=new $this->carrierClassName();
	}
}

class infoX {	// information exchange layer
	function __construct() {
		$this->childObjects=Array( "accounting" , "cart" );
	} // construct
	
	public function __call($name, $arguments){ 
		foreach( $this->childObjects as $objname )
			if( @in_array($name,get_class_methods($this->$objname))  )
				$this->$objname->$name();
	}

	function set_accounting( $class="" ){
		if( strlen( $class ) > 2 )
			$this->accountingClassName=$class;
		$this->accounting=new $this->accountingClassName();
	}

}
// implements infoX methods to get info from xTuple accounting
class xTuple extends infoX {	
	function __construct() { 
		// connect to xTuple's postgres database
	}
	function selectAnOrder(){	// this should populate shipping with all the infos?
		echo "Hi from inside the xTuple class, my method name is: ".__FUNCTION__."<br>\n";
	}
	function updateAnOrder() {	// write the tracknum and shipping cost back to the invoice
		echo "Hi from inside the xTuple class, my method name is: ".__FUNCTION__."<br>\n";
	}
	function getShippableOrders() {	// list of orders marked for shipping, etc
		echo "Hi from inside the xTuple class, my method name is: ".__FUNCTION__."<br>\n";
	}
} 

class Ups {		// code in here for talking to ups's web xml api
	function __construct() { 
		// set up UPS defaults and DEFINEs ... 
	}
} ?>[/PHP]

Then at the user's level, all you have to do is include whatever file the Ship class is declared. In the production code, I have it then also include the Ups, xTuple, etc files for those class definitions.

Here's what the web programmer types:
[PHP]<?
$s = new Ship;

$s->getShippableOrders();
$s->selectAnOrder();
?>
[/PHP] 

And from the above php code, this is the output:
```
Hi from inside the xTuple class, my method name is: getShippableOrders

Hi from inside the xTuple class, my method name is: selectAnOrder
```

---

