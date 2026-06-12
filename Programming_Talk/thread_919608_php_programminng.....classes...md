---
title: "php programminng.....classes.."
date: 2008-09-14
forum: Programming Talk
---

### Post by hockey97 on 2008-09-14
Ok, I am trying to learn how to use classes in php.

I googled around and found very limited stuff on this.

so far this is what I understand.

here is an example:

[PHP]var $money; 
var $sales_tax=6%;
class cashier{
function cash_register(){
$this->money=$_POST["cash"];
$this->sales_tax=$money*6%;
$payment=$this->money+$this->sale_tax;
echo"$payment";
}
}
[/PHP]

I would like for someone to explain to point out a website that can fully explain how to create a class and also use it.

I currently tried doing this but failed getting undefined method  errors.

this is how I was told to implement these classes to another php file:

[PHP]$cashier1= new cashier;
//then I would just use the function in the class
$cashier1->cash_register();[/PHP]


I am sure I am doing somthing wrong.

---

### Post by extruct on 2008-09-14
Well If you are familiar with C programming language then you should know the meaning of Struct. So Class is basically struct with functions.
If you don't know C and don't know what struct is than I'll try to explain:
In the real world you can refer to everything as Object. A good example is Car, it has **Characteristics** and **methods**. Example of cars characteristic: color = red, max speed = 200km/h, type = sport and etc. Example of methods = turn engine on, turn left, turn right, stop and etc.
To allow people to refer to a set of characteristics and methods as object class was invented. As you understood class is a set of characteristics and methods. Example:
```

class Car{
  private $color;
  private $max_speed;
  public $name;
  ...

  function __construct($color, $max_speed){
    $this->color = $color;
    $this->max_speed = max_speed;
    $this->name = 'generic car';
  }

  function print_info(){
    echo 'I\m a ' . $this->color . ' ' . $this->name . ' car with top speed of ' . $this->max_speed . 'Km/H';
  }

  function turn_on_engine(){ ... }
  function turn_left(){ ... }
  ...
}
```
Now you have object that describes car. In order to create an instance of car you use:
```

$ferrari = new Car('red', 200);
$bug = new Car('yellow', 50);

$ferrari->name = 'Ferrari';

$ferrari->print_info();
$bug->print_info();

```
Here you created 2 instances of car but with different characteristics.
Code explanation:
```

private $color;
private $max_speed;
public $name;

```
This lines define an inside variables of class.
Difference between private and public:
private allows access to this variables only inside the class therefor this line $ferrari->color = 'blue'; will generate an error because color is private and can be accessed only by class methods. Public can be accessed from inside the class but also from outside therefor $ferrari->name = 'Ferrari'; wont generate error because name is public (there are also protected variables but lets leave it for now).
After we done defining variables we start define functions (or methods)
__construct()
Construct is a magic function, it called in the moment you create a new instance of class, its handy for setting default variables values if needed. So our construct receives 2 parameters, color and speed.
In order to access from the class to classes variable we use the variable $this. Its like a pointer to the class itself (also can be used of functions, like $this->do_foo();) $this available only inside class. After the construct we define addition methods of the class.

```

$ferrari = new Car('red', 200);
$bug = new Car('yellow', 50);

$ferrari->name = 'Ferrari';

$ferrari->print_info();
$bug->print_info();

```
First two lines create Instances of the car giving the unique characteristic (color and speed). 3th line we set ferraris name to Ferrari (name is a public therefor we can access to it outside of the class). Then we execute the print_info() method.

I tried shortly to explain about classes hope it helped somehow, feel free to ask more questions :)
Good luck :)

P.S. You can check php.net for tutorials there are also tutorials about OOP.

---

### Post by hockey97 on 2008-09-14
I think I fully understand the concept and now understood fully what classes are.

SO it's  like  making a programmed object that can be used repeatedly.

like that car example it's a class of functions and vars that is in some way about or involved with the car on the type of car and how it functions.

so classes are more like generalizing cars but could be used for specific cars. 

if I were to make a game of a city and had cars on the roads. I could make one car class but used it for each different car.

so every car is using the same class but yet they can vary depending on how the class was made and what was inputted into the copy of the class.


I understand it now. I am going to look at php Manuel to read more on classes for php.

---

### Post by CptPicard on 2008-09-14
I think you pretty much got it but let's put it in simpler terms still...

A class is a collection of data and functions that operate on that data. Classes are "used" by *instantiating objects* that are of the type of that class. So your actual car items in your hypothetical driving game are not "classes" but *objects* of the class Car...

These different objects can then have different values for their data, such as registration number, location, owner name... but they all behave the same, according to the code defined in the class, when you for example drive() them.

---

### Post by hockey97 on 2008-09-14
Thanks I understand now. I also just found a website that would give explains what classes are and how to use them in php.

SO I will post it here if anyone else has problems learning classes with php since I notice there isn't muct stuff on php on the net it's very limited.

I know c++ and c they have alot of websites that do explain classes. 

here is the link:[http://www.phpbuilder.com/columns/rod19990601.php3]("http://www.phpbuilder.com/columns/rod19990601.php3")

---

### Post by pedrotuga on 2008-09-14
For everything that concerns PHP, you have the official documentation at [http://php.net](http://php.net). No other site or book beats that.

ATM php has two implementations of object oriented programming support.
I don't know for how long PHP's OOP has been around. What i know is that it has been rewritten in PHP5 because it was lacking some features.

I recommend you learn both. It really doesn't take that long to read those docs.


[http://se2.php.net/manual/en/language.oop.php](http://se2.php.net/manual/en/language.oop.php)

[http://se2.php.net/manual/en/language.oop5.php](http://se2.php.net/manual/en/language.oop5.php)

---

