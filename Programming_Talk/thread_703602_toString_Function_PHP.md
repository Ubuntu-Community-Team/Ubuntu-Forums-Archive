---
title: "toString Function PHP"
date: 2008-02-21
forum: Programming Talk
---

### Post by Das Oracle on 2008-02-21
Hello everyone.

I am having a bit of difficulty with creating a toString() function in php. I have a class called Client in client.php which contains a tostring method i wrote. If I am in another php file and trying to call this method I get 0 returned by the function. It will not return the data that is supposedly stored in the object. I can write the object to the database and all the information is there, so I was wondering if anyone had any idea on what was going on.

Client.php
```
class Client{
	private $firstname;
	private $lastname;
	private $address;
	private $city;
	private $state;
	private $zip;
	private $primaryphone;
	private $secondaryphone;
	private $email;
	
	public function _construct
	(
		$cl_first,
		$cl_last,
		$cl_add,
		$cl_city,
		$cl_state,
		$cl_zip,
		$cl_pphone,
		$cl_sphone,
		$email
	){
		$this->firstname = $cl_first;
		$this->lastname = $cl_last;
		$this->address = $cl_add;
		$this->city = $cl_city;
		$this->state = $cl_state;
		$this->zip = $cl_zip;
		$this->primaryphone = $cl_pphone;
		//$this->secondaryphone = $cl_sphone;
		$this->email = $cl_email;
	}
	
	public function getfirstname(){return $firstname;}
	public function getlastname(){return $lastname;}
	public function getaddress(){return $address;}
	public function getcity(){return $city;}
	public function getstate(){return $state;}
	public function getzip(){return $zip;}
	public function getprimaryphone(){return $primaryphone;}
	public function getsecondaryphone(){return $secondaryphone;}
	public function getemail(){return $email;}
	
	public function setfirstname($first){$this->firstname = $first;}
	public function setlastname($last){$this->lastname = $last;}
	public function setaddress($address){$this->address = $address;}
	public function setcity($city){$this->city = $city;}
	public function setstate($state){$this->state = $state;}
	public function setzip($zip){$this->zip = $zip;}
	public function setprimaryphone($pphone){$this->primaryphone = $pphone;}
	public function setsecondaryphone($sphone){$this->secondaryphone = $sphone;}
	public function setemail($email){$this->email = $email;}
	
	public function toString(){return $firstname+", "+$lastname+", "+$address+", "+$city+", "+$state+", "+$zip+", "+$primaryphone+", "+$secondaryphone+", "+$email;}
```

and here is the usage of it in another php file *note that i already have client.php included into this php file:

```
print $customer.toString();
//$customer = serialize($customer);
$query = "INSERT INTO client(client) Values('$customer')";
mysql_query($query) or die(mysql_error);
```

---

### Post by mike_g on 2008-02-21
instead of: $firstname
Shouldent it be: $this->firstname

etc.

---

### Post by Das Oracle on 2008-02-21
I am not sure what part you are referring to? I tried using 'this' in the get functions and in tostring but the result was still the same.

---

### Post by hakre on 2008-12-05
maybe you are looking for the magic methid __toString():

[http://de2.php.net/manual/en/language.oop5.magic.php](http://de2.php.net/manual/en/language.oop5.magic.php)

---

