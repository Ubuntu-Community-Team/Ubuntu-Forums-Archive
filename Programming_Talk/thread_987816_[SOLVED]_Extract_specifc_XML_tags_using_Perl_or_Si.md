---
title: "[SOLVED] Extract specifc XML tags using Perl or Similar"
date: 2008-11-19
forum: Programming Talk
---

### Post by jonobr on 2008-11-19
Hi All,

Im no programmer but Im trying to do something which I know should be simple, Ive toyed around a tiny bit with bash scripting, sed and perl , and Im terrible at it.

Ive got a raw xml file which has recurring information.
Im trying to grab key fields using the tags and place them on a seperate comma or tab delimited file,
I know theres probably a number of posts here that may do the trick and squillions on the internet, but I cant seem to find anything useful. If anyone has any examples or good howto guides.

Heres a very crude example


<PersonName>
	<FirstName>jonobr</FirstName>
	<LastName>ubuntu</LastName>
</PersonName>
<AddressDetails>
	<Country>
		<CountryNameCode>US</CountryNameCode>
		<CountryName>United States</CountryName>
		<AdministrativeAreaName>Colorado</AdministrativeAreaName>
		<LocalityName>Denver</LocalityName>
	</Country>
</AddressDetails>
<PersonName>
	<FirstName>Jimbo</FirstName>
	<LastName>Hardy</LastName>
</PersonName>
<AddressDetails>
	<Country>
		<CountryNameCode>CN</CountryNameCode>
		<CountryName>Canada</CountryName>
		<AdministrativeAreaName>BC</AdministrativeAreaName>
		<Locality><LocalityName>Toronto</LocalityName>
	</Country>
</AddressDetails>


Extract Firstname Country name code and locality
This will give

jonobr,US,Denver
jimbo,CN,Toronto

And on until there is no more information.

---

### Post by pmasiar on 2008-11-19
Python with ElementTree (lxml.etree, since Py2.5) is the easierst way, by far.

---

### Post by jonobr on 2008-11-20
MMmmm

Thanks for the info.
Ill kick the tires on that tomorrow and see how it shakes out.

Thanks!

---

### Post by jonobr on 2008-12-02
Hello


I managed to get a workable solution in place using xml2csv, and even better there is a version available for the Windows OS, which allows me to get someone else to do this who is not linux savvy.

THe tricky part for me was coming up with the format.txt file to aprse what I needed , but now it is operational.

Thanks

---

