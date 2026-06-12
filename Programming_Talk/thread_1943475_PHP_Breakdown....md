---
title: "PHP Breakdown..."
date: 2012-03-19
forum: Programming Talk
---

### Post by SBLMsurfer on 2012-03-19
I've been trying to teach myself PHP in my downtime, but I've come across a piece of script that I can't seem to grasp.  I've looked up different explanations, but I still can't quite figure out the logic and why it's used at all.  I think I would understand a bit more if someone possibly broke it down for me, and told me how/why it's useful...

[PHP]public function __construct( $data=array() ) {
    if ( isset( $data['id'] ) ) $this->id = (int) $data['id'];
    if ( isset( $data['publicationDate'] ) ) $this->publicationDate = (int) $data['publicationDate'];
    if ( isset( $data['title'] ) ) $this->title = preg_replace ( "/[^\.\,\-\_\'\"\@\?\!\:\$ a-zA-Z0-9()]/", "", $data['title'] );
    if ( isset( $data['summary'] ) ) $this->summary = preg_replace ( "/[^\.\,\-\_\'\"\@\?\!\:\$ a-zA-Z0-9()]/", "", $data['summary'] );
    if ( isset( $data['content'] ) ) $this->content = $data['content'];
  }[/PHP]

I do NOT understand Construct functions... and I don't understand why you would declare something like $this->id... I just am not getting this part.

Any explanations would be greatly appreciated....

---

### Post by dharmavir on 2012-03-24
Constructors are concept which was brought by object oriented programming model. Constructors are integral part of Class where you define constructors so that when class gets initialized they are called first and does the job of primary setup for the object of setting property and so forth.

Now as I understand you need to brush up your programming concept from the ground zero I would suggest you to read some book like suggested below:

[http://www.amazon.com/Object-Oriented-Programming-C-4th-Edition/dp/0672323087/ref=sr_1_1?ie=UTF8&qid=1332601355&sr=8-1](http://www.amazon.com/Object-Oriented-Programming-C-4th-Edition/dp/0672323087/ref=sr_1_1?ie=UTF8&qid=1332601355&sr=8-1)

or some beginner book for programming.

---

### Post by dharmavir on 2012-03-24
Forgot to write about $this->variable;

When you see some variable inside a class being referred as $this->variableName, it means that "variableName" is member variable (or property) of that class and in future object.

Now if you have question about class and object then let me explain you:

Class is like a die [http://en.wikipedia.org/wiki/Die_(manufacturing](http://en.wikipedia.org/wiki/Die_(manufacturing)), and object is like real object in hand which comes out of as defined in die.

I hope that makes sense.

---

### Post by generic41209 on 2012-03-24
You'll find constructors in many languages. They are used so that you can declare an instance of an object, especially when you want to instruct the program how to handle it when different variables are fed to it.

See my comments within your php code

[PHP]//public functions can be called outside the class (you probably have a class outside of this chunk of script
//function is a set of code that can be reused by calling it from other places in the script. It does not get executed if it is not called.
// This function accepts an array as an argument. It calles the array $data when it is used within the function
public function __construct( $data=array() ) {
    //isset is a php native funsction, you can look it up on the php reference pages. It returns a boolean value, so in this case if the value is set, then the following code gets executed, if the variable, or the 'id' attribute in the data array is set.
    //"this" means that you are referring to this instance of the object, hence my statement earlier that there is more code encapsulating this. So, "this"->id is the variable $id in the declared class of this instance.
    if ( isset( $data['id'] ) ) $this->id = (int) $data['id'];
    if ( isset( $data['publicationDate'] ) ) $this->publicationDate = (int) $data['publicationDate'];
    //preg_replace is also a native php function, it is used to replace text. It ulilizes regex expressions, which is all the garbage you see folowing.
    if ( isset( $data['title'] ) ) $this->title = preg_replace ( "/[^\.\,\-\_\'\"\@\?\!\:\$ a-zA-Z0-9()]/", "", $data['title'] );
    if ( isset( $data['summary'] ) ) $this->summary = preg_replace ( "/[^\.\,\-\_\'\"\@\?\!\:\$ a-zA-Z0-9()]/", "", $data['summary'] );
    if ( isset( $data['content'] ) ) $this->content = $data['content'];
  } [/PHP]

---

