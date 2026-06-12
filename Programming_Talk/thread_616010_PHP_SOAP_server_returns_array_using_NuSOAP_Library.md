---
title: "PHP SOAP server returns array using NuSOAP Library"
date: 2007-11-17
forum: Programming Talk
---

### Post by mohtasham1983 on 2007-11-17
Hi,
I have a function in my SOAP server that returns an array. When the client calls this function, it only receives "array", and when I use foreach to print each member of this array, it tells me that this is not an array. If I change the returned value of the function to a string or integer type everything works fine though, so I don't think that there is any problem with the client.

I am using NuSOAP library on php to achieve that.

I had doubt when declaring the type of return value of the function. In XML schema there is no array type, so I specified the return value as a string like this:

[PHP]$server->register("getLocation",
                array('country_population' => 'xsd:string',
                'city_population' => 'xsd:string'),
                array ('return' => 'xsd:string'),
                'urn:world',
                'urn:worldquote#getLocation'); [/PHP]

The return values is a result of a query from database.

Any idea how I can declare array element in XML schema?

---

