---
title: "Script for CGI batch submit"
date: 2010-10-19
forum: Programming Talk
---

### Post by kg1128 on 2010-10-19
hi, i need to access the following online database:
 
[http://ssdi.rootsweb.ancestry.com/cgi-bin/ssdi.cgi](http://ssdi.rootsweb.ancestry.com/cgi-bin/ssdi.cgi)
 
using SSN as an input, you can search whether the associated person is dead or not.
 
i want to write a local program that takes a list of SSNs in a text file as an input, then run each query using the online death database, and writes each result in an output file. any help would be much appreciated!

---

### Post by amauk on 2010-10-19
You'll need to construct the POST data to send to the form, then filter the resulting HTML response

To send the query to the form, do something like this
```
wget -q --post-data "key1=val1&key2=val2&key3=val3" -O - "http://ssdi.rootsweb.ancestry.com/cgi-bin/ssdi.cgi"
```

This will send the data
key1 = val1
key2 = val2
key3 = val3
to the form located at
[http://ssdi.rootsweb.ancestry.com/cgi-bin/ssdi.cgi](http://ssdi.rootsweb.ancestry.com/cgi-bin/ssdi.cgi)


The key/value pairs are taken direct from the HTML page

Quickly filtering out all the form data, you get
```
<form name="ssdiform" method="post" action="/cgi-bin/ssdi.cgi">

<input type="hidden" name="so" value="sa"/>

<input type="text" maxlength="20" size="20" id="sn" name="sn" tabindex="1" value="" />

<select name="nt">
    <option value="exact" selected="selected">Exact</option>
    <option value="soundex">Soundex</option>
    <option value="metaphone">Metaphone</option>
</select>

<input type="text" maxlength="15" size="15" id="fn" name="fn" tabindex="2" value="" />

<input type="text" maxlength="15" size="15" id="mn" name="mn" tabindex="3" value="" />

<input type="text" name="byr" size="4" maxlength="4" value="" tabindex="4"/>

<select name="rbyr">
    <option value="0" selected="selected">Exact</option>
    <option value="1">+/- 1 year</option>
    <option value="2">+/- 2 years</option>
    <option value="3">+/- 3 years</option>
    <option value="4">+/- 4 years</option>
    <option value="5">+/- 5 years</option>
    <option value="10">+/- 10 years</option>
</select>

<select name="bmo" tabindex="5">
    <option value="00">Any</option>
    <option value="01">Jan</option>
    <option value="02">Feb</option>
    <option value="03">Mar</option>
    <option value="04">Apr</option>
    <option value="05">May</option>
    <option value="06">Jun</option>
    <option value="07">Jul</option>
    <option value="08">Aug</option>
    <option value="09">Sep</option>
    <option value="10">Oct</option>
    <option value="11">Nov</option>
    <option value="12">Dec</option>
</select>

<select name="bdy" tabindex="6">
    <option value="00">Any</option>
    <option value="01">1</option>
    <option value="02">2</option>
    <option value="03">3</option>
    <option value="04">4</option>
    <option value="05">5</option>
    <option value="06">6</option>
    <option value="07">7</option>
    <option value="08">8</option>
    <option value="09">9</option>
    <option value="10">10</option>
    <option value="11">11</option>
    <option value="12">12</option>
    <option value="13">13</option>
    <option value="14">14</option>
    <option value="15">15</option>
    <option value="16">16</option>
    <option value="17">17</option>
    <option value="18">18</option>
    <option value="19">19</option>
    <option value="20">20</option>
    <option value="21">21</option>
    <option value="22">22</option>
    <option value="23">23</option>
    <option value="24">24</option>
    <option value="25">25</option>
    <option value="26">26</option>
    <option value="27">27</option>
    <option value="28">28</option>
    <option value="29">29</option>
    <option value="30">30</option>
    <option value="31">31</option>
</select>

<input type="text" name="dyr" size="4" maxlength="4" value="" tabindex="7"/>

<select name="rdyr">
    <option value="0" selected="selected">Exact</option>
    <option value="1">+/- 1 year</option>
    <option value="2">+/- 2 years</option>
    <option value="3">+/- 3 years</option>
    <option value="4">+/- 4 years</option>
    <option value="5">+/- 5 years</option>
    <option value="10">+/- 10 years</option>
</select>

<select name="dmo" tabindex="8">
    <option value="00">Any</option>
    <option value="01">Jan</option>
    <option value="02">Feb</option>
    <option value="03">Mar</option>
    <option value="04">Apr</option>
    <option value="05">May</option>
    <option value="06">Jun</option>
    <option value="07">Jul</option>
    <option value="08">Aug</option>
    <option value="09">Sep</option>
    <option value="10">Oct</option>
    <option value="11">Nov</option>
    <option value="12">Dec</option>
</select>

<select name="ddy" tabindex="8">
    <option value="00">Any</option>
    <option value="01">1</option>
    <option value="02">2</option>
    <option value="03">3</option>
    <option value="04">4</option>
    <option value="05">5</option>
    <option value="06">6</option>
    <option value="07">7</option>
    <option value="08">8</option>
    <option value="09">9</option>
    <option value="10">10</option>
    <option value="11">11</option>
    <option value="12">12</option>
    <option value="13">13</option>
    <option value="14">14</option>
    <option value="15">15</option>
    <option value="16">16</option>
    <option value="17">17</option>
    <option value="18">18</option>
    <option value="19">19</option>
    <option value="20">20</option>
    <option value="21">21</option>
    <option value="22">22</option>
    <option value="23">23</option>
    <option value="24">24</option>
    <option value="25">25</option>
    <option value="26">26</option>
    <option value="27">27</option>
    <option value="28">28</option>
    <option value="29">29</option>
    <option value="30">30</option>
    <option value="31">31</option>
</select>

<input type="text" name="lazip" value="" size="5" maxlength="5" tabindex="10" />

<input type="text" name="lacity" value="" size="20" tabindex="11" />

<input type="text" name="lacounty" value="" size="20" tabindex="12" />

<input type="text" name="lastate" value="" size="2" maxlength="2" tabindex="13" />

<input type="text" name="luzip" value="" size="5" maxlength="5" tabindex="14" />

<input type="text" name="lucity" value="" tabindex="15" />

<input type="text" name="lucounty" value="" tabindex="16" />

<input type="text" name="lustate" value="" size="2" maxlength="2" tabindex="17" />

<input type="text" name="ssn1" size="3" maxlength="3" value="" tabindex="18" /> - 

<input type="text" name="ssn2" size="2" maxlength="2" tabindex="19" value="" /> - 

<input type="text" name="ssn3" tabindex="20" size="4" maxlength="4" value="" />

<select name="issue" tabindex="21">
    <option value="" selected="selected">Any</option>
    <option value="Alabama">Alabama</option>
    <option value="Alaska">Alaska</option>
    <option value="American Somoa">American Somoa</option>
    <option value="Arizona">Arizona</option>
    <option value="Arkansas">Arkansas</option>
    <option value="California">California</option>
    <option value="Colorado">Colorado</option>
    <option value="Connecticut">Connecticut</option>
    <option value="Delaware">Delaware</option>
    <option value="District of Columbia">District of Columbia</option>
    <option value="Florida">Florida</option>
    <option value="Georgia">Georgia</option>
    <option value="Guam">Guam</option>
    <option value="Hawaii">Hawaii</option>
    <option value="Idaho">Idaho</option>
    <option value="Illinois">Illinois</option>
    <option value="Indiana">Indiana</option>
    <option value="Iowa">Iowa</option>
    <option value="Kansas">Kansas</option>
    <option value="Kentucky">Kentucky</option>
    <option value="Long-time or retired railroad workers">Long-time or retired railroad workers</option>
    <option value="Louisiana">Louisiana</option>
    <option value="Maine">Maine</option>
    <option value="Maryland">Maryland</option>
    <option value="Massachusetts">Massachusetts</option>
    <option value="Michigan">Michigan</option>
    <option value="Minnesota">Minnesota</option>
    <option value="Mississippi">Mississippi</option>
    <option value="Missouri">Missouri</option>
    <option value="Montana">Montana</option>
    <option value="Nebraska">Nebraska</option>
    <option value="Nevada">Nevada</option>
    <option value="New Hampshire">New Hampshire</option>
    <option value="New Jersey">New Jersey</option>
    <option value="New Mexico">New Mexico</option>
    <option value="New York">New York</option>
    <option value="North Carolina">North Carolina</option>
    <option value="North Dakota">North Dakota</option>
    <option value="Ohio">Ohio</option>
    <option value="Oklahoma">Oklahoma</option>
    <option value="Oregon">Oregon</option>
    <option value="Pennsylvania">Pennsylvania</option>
    <option value="Philippine Islands">Philippine Islands</option>
    <option value="Puerto Rico">Puerto Rico</option>
    <option value="Rhode Island">Rhode Island</option>
    <option value="South Carolina">South Carolina</option>
    <option value="South Dakota">South Dakota</option>
    <option value="Tennessee">Tennessee</option>
    <option value="Texas">Texas</option>
    <option value="Utah">Utah</option>
    <option value="Vermont">Vermont</option>
    <option value="Virgin Islands">Virgin Islands</option>
    <option value="Virginia">Virginia</option>
    <option value="Washington">Washington</option>
    <option value="West Virginia">West Virginia</option>
    <option value="Wisconsin">Wisconsin</option>
    <option value="Wyoming">Wyoming</option>
</select>

<input type="text" name="age" value="" size="3" maxlength="3" tabindex="22" />

<select name="rage">
    <option value="0" selected="selected">Exact</option>
    <option value="1">+/- 1 year</option>
    <option value="2">+/- 2 years</option>
    <option value="3">+/- 3 years</option>
    <option value="4">+/- 4 years</option>
    <option value="5">+/- 5 years</option>
    <option value="10">+/- 10 years</option>
</select>

<input type="submit" name="sb" value="Submit" class="btn2" tabindex="32" />
```


You'll need to build up a standard set of key/value pairs, with some variables for things you want to change (name, etc.)

So the end query will look like this
```
#!/bin/bash

FIRST_NAME="$1"
LAST_NAME="$2"

RESULT=$(wget -q --post-data "so=sa&sn=${LAST_NAME}&fn=${FIRST_NAME}&........" -O - "http://ssdi.rootsweb.ancestry.com/cgi-bin/ssdi.cgi")
```

Then comes the interpretation on the resulting HTML response page, which hopefully should be no more than grepping for alive or dead?

---

### Post by kg1128 on 2010-10-19
thank you so much!

---

