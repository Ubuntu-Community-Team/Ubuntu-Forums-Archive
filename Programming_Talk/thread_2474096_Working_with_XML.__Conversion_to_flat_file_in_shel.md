---
title: "Working with XML.  Conversion to flat file in shell script.   What utilities?"
date: 2022-04-21
forum: Programming Talk
---

### Post by chris53 on 2022-04-21
Hi There.    I recently have been trying to get Pandas installed on Ubuntu 20.04.    This is for parsing XML files into CSV files in a python script.    Problem is Pandas has not been very straight forward of an install.
I'm new to working with XML.  And yes I need to do it in a script.   I will be processing a lot of XML files.    My question is what utility do you use to parse XML or how were you able to get Pandas installed on Ubuntu 20.04.

Thank you,
Chris

---

### Post by TheFu on 2022-04-21
```
sudo apt-get install python3-pandas
```
not working?  That's what the project page says to use.

I had to convert JSON into XML last fall.  Slurping JSON was relatively easy in Perl.  Due to some required translations from the inputs to the required output format, I simple looped over the internal structure and created XML using printf lines ... after performing the xyz --> 1.3.5 translations for about 20 different data types.

To slurp the json file was 1 line:
```
my $json_text = decode_json($json_file);
```
json_text became a pointer to all the structures inside the json which could be looped over as I moved deeper into the nested structures. I have lots of code, but since it is json and perl, I doubt it would be too helpful.

I bet slurping an XML file would be pretty much the same, as would looping and accessing the deeper, nested, structures.  Pretty common stuff.
The json parser came with a dumper program which would output the JSON in a pretty format, but since JSON order isn't guaranteed, it can be a messy text file.

---

### Post by chris53 on 2022-04-22
> **TheFu said:**
> ```
sudo apt-get install python3-pandas
```
not working?  That's what the project page says to use.


Nope,  Doesnt work.   Very strange.   I've tried a couple things including this.   I REALLY don't like the feeling of installing something on my machine and then it doesn't work.   Makes me wonder what did I just install....  

Any ideas?

Thanks,
Chris

---

### Post by #&amp;thj^% on 2022-04-22
just my attempt to help, would something like this work for now.
say i have a file:
```
<?xml version='1.0' encoding='UTF-8' ?>
<DataFile xmlns:xsi='http://www.w3.org/2001/XMLSchema-instance' contactCount='4999' date='2012-04-14' time='22:00:14' xsi:noNamespaceSchemaLocation='gen
.xsd'>
<Contact id="1">
  <Name>
    <FirstName>CHERLY</FirstName>
    <LastName>MORGA</LastName>
  </Name>
  <Address>
    <Street>401 </Street>
    <City>TRINIDAD</City>
    <State>CO</State>
    <Zip>81082</Zip>
  </Address>
  <ContactInfo>
    <Email>morga@msn.com</Email>
    <EvePhone>719-1</EvePhone>
  </ContactInfo>
  <Activity date="2012-04-04" source="Business Center" subSource="ES 2012 BC  22461" tdm_seq_num="EF_14832004" time="1
0:48:54">
    <Product>
      <POI code="15866" year="2012"/>
      <POI code="1-1ED0DJ" year="2012"/>
    </Product>
    <Survey>
      <Question1>
        <Response>4-6 months</Response>
      </Question1>
      <Question2>
        <Response>Moab, UT</Response>
      </Question2>
      <Question3>
        <Response>N</Response>
      </Question3>
      <Question4>
        <Response>No</Response>
      </Question4>
    </Survey>
  </Activity>
</Contact>
<Contact id="2">
  <Name>
    <FirstName>Gur</FirstName>
    <LastName>Singh</LastName>
  </Name>
  <Address>
    <Street>Garrison</Street>
    <City>Jersey City</City>
    <State>NJ</State>
    <Zip>07306</Zip>
  </Address>
  <ContactInfo>
    <Email>gursingh@gmail.com</Email>
    <EvePhone>2019</EvePhone>
  </ContactInfo>
  <Activity date="2012-04-05" source="Autoshow" subSource="ES 2012 Marketing 22402" tdm_seq_num="EF_14837438" time="
14:23:50">
    <Product/>
    <Survey>
      <Question1>
        <Response>Undecided</Response>
      </Question1>
      <Question2>
        <Response>New York, NY</Response>
      </Question2>
      <Question3>
        <Response>Y</Response>
      </Question3>
      <Question4>
        <Response>No</Response>
      </Question4>
    </Survey>
  </Activity>
</Contact>
</DataFile>
```
when I just use:
```
perl -nle 'BEGIN{print "ID\tEmail\tsubsource";} if (/Contact id(\s+=|=)(\s+\"|\")(.+?)\"/) {printf "%s\t",$3} if (/subSource(\s+=|=)(\s+"|")(.+?)\"/){printf "%s\n",$3} if(/<Email>(.+?)<\/Email>/){printf "%s\t",$1}'  filename
```
results in:
```
ID	Email	subsource
1	morga@msn.com	ES 2012 BC  22461
2	gursingh@gmail.com	ES 2012 Marketing 22402

```

---

### Post by chris53 on 2022-04-24
[QUOTEwhen I just use:
```
perl -nle 'BEGIN{print "ID\tEmail\tsubsource";} if (/Contact id(\s+=|=)(\s+\"|\")(.+?)\"/) {printf "%s\t",$3} if (/subSource(\s+=|=)(\s+"|")(.+?)\"/){printf "%s\n",$3} if(/<Email>(.+?)<\/Email>/){printf "%s\t",$1}'  filename
```
results in:
```
ID    Email    subsource
1    morga@msn.com    ES 2012 BC  22461
2    gursingh@gmail.com    ES 2012 Marketing 22402

```[/QUOTE]

[/QUOTE]

Sure that would work, but its not using an XML utility.   I am starting to process RSS feeds, some I receive 3x a day and would much prefer using an XML utiility like Pandas (or something similar) which the coding to covert an XML file to CSV is simple.
But for some reason I cant get the damn plug-in to install properly.  

Thanks for the reply though :)

---

### Post by TheFu on 2022-04-24
I don't use python, but a multi-stage solution can work.
Convert the XML into HTML, then convert the "pretty" HTML into text (not 1 line jammed together), then use whatever tools you like to pull the specific parts out that you like.

In Perl, I'd use an XML module to slurp the file in to RAM, organized, then loop over the specific types of data I want to export, then use a 'tie' class to a CSV/TSV file (I like tabs as delimiters) to dump it.
If the XML isn't ugly (1 line only), then the quickest answer is a mix of grep and sed commands.

If you are getting RSS, then I'd use a module specific to RSS data. It has a standard and there are modules for it for both .rss and .atom formats. 
Google found this python answer:
```
import feedparser
NewsFeed = feedparser.parse("https://timesofindia.indiatimes.com/rssfeedstopstories.cms")
entry = NewsFeed.entries[1]

print entry.keys()
```
To me, looks like that code is missing some ';', but that's a difference between perl and python, I suppose.

---

### Post by chris53 on 2022-04-25
> **TheFu said:**
> If you are getting RSS, then I'd use a module specific to RSS data. It has a standard and there are modules for it for both .rss and .atom formats.


Yeah, its an RSS feed.   NOAA weather in my area.   I am building  a weather station with Arduino.   I'll look for an RSS specific XML parser.   Thanks for the tip.   This is kindof annoying!!  lol

Here is a sample of what I want to parse.   Just some of the fields in to a csv..

<?xml version="1.0" encoding="ISO-8859-1"?> 
<?xml-stylesheet href="latest_ob.xsl" type="text/xsl"?>
<current_observation version="1.0"
     xmlns:xsd="http://www.w3.org/2001/XMLSchema"
     xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
     xsi:noNamespaceSchemaLocation="http://www.weather.gov/view/current_observation.xsd">
    <credit>NOAA's National Weather Service</credit>
    <credit_URL>https://weather.gov/</credit_URL>
    <image>
        <url>https://weather.gov/images/xml_logo.gif</url>
        <title>NOAA's National Weather Service</title>
        <link>https://www.weather.gov</link>
    </image>
    <suggested_pickup>15 minutes after the hour</suggested_pickup>
    <suggested_pickup_period>60</suggested_pickup_period>
    <location>Tampa, Tampa International Airport, FL</location>
    <station_id>KTPA</station_id>
    <latitude>27.96139</latitude>
    <longitude>-82.54028</longitude>
    <observation_time>Last Updated on Apr 16 2022, 12:53 pm EDT</observation_time>
        <observation_time_rfc822>Sat, 16 Apr 2022 12:53:00 -0400</observation_time_rfc822>
    <weather>Partly Cloudy</weather>
    <temperature_string>82.0 F (27.8 C)</temperature_string>
    <temp_f>82.0</temp_f>
    <temp_c>27.8</temp_c>
    <relative_humidity>65</relative_humidity>
    <wind_string>Southwest at 6.9 MPH (6 KT)</wind_string>
    <wind_dir>Southwest</wind_dir>
    <wind_degrees>240</wind_degrees>
    <wind_mph>6.9</wind_mph>
    <wind_kt>6</wind_kt>
    <pressure_string>1017.3 mb</pressure_string>
    <pressure_mb>1017.3</pressure_mb>
    <pressure_in>30.04</pressure_in>
    <dewpoint_string>69.1 F (20.6 C)</dewpoint_string>
    <dewpoint_f>69.1</dewpoint_f>
    <dewpoint_c>20.6</dewpoint_c>
    <heat_index_string>85 F (29 C)</heat_index_string>
          <heat_index_f>85</heat_index_f>
          <heat_index_c>29</heat_index_c>
    <visibility_mi>10.00</visibility_mi>
     <icon_url_base>https://forecast.weather.gov/images/wtf/small/</icon_url_base>
    <two_day_history_url>https://www.weather.gov/data/obhistory/KTPA.html</two_day_history_url>
    <icon_url_name>sct.png</icon_url_name>
    <ob_url>https://www.weather.gov/data/METAR/KTPA.1.txt</ob_url>
    <disclaimer_url>https://www.weather.gov/disclaimer.html</disclaimer_url>
    <copyright_url>https://www.weather.gov/disclaimer.html</copyright_url>
    <privacy_policy_url>https://www.weather.gov/notice.html</privacy_policy_url>
</current_observation>

---

### Post by TheFu on 2022-04-26
[https://wiki.python.org/moin/RssLibraries](https://wiki.python.org/moin/RssLibraries) seems to have an example for reading the feed.  They don't show a full solution. 

The perl guys show a full solution. They show getting, parsing and printing the different fields.  Basically, to solve the problem above, only the print line would need to be modified. [https://metacpan.org/pod/XML::RSS::Parser::Lite](https://metacpan.org/pod/XML::RSS::Parser::Lite)  I like how the perl guys get to the point, fast.

---

### Post by chris53 on 2022-04-26
> **TheFu said:**
> [https://wiki.python.org/moin/RssLibraries](https://wiki.python.org/moin/RssLibraries) seems to have an example for reading the feed.  They don't show a full solution. 

The perl guys show a full solution. They show getting, parsing and printing the different fields.  Basically, to solve the problem above, only the print line would need to be modified. [https://metacpan.org/pod/XML::RSS::Parser::Lite](https://metacpan.org/pod/XML::RSS::Parser::Lite)  I like how the perl guys get to the point, fast.

Cool,  I will check it out.   So far, this is what I have found.    This is Python with Pandas..    Its not perfect,  I'm trying to figure out what its doing and modify accordingly.   Seems the examples I am finding is specific to the source being processed which I guess makes sense.  

The code:
############################################################################################################################
import xml.etree.ElementTree as ET
import pandas as pd


xml_data = open('/home/cwegescheide/Desktop/Development/Datafiles/SrcFiles/NOAA_Tampa_Weather_2022-04-21-051501.XML', 'r').read()  # Read file
root = ET.XML(xml_data)  # Parse XML


data = []
cols = []
for i, child in enumerate(root):
data.append(child.text)
    cols.append(child.tag)


df = pd.DataFrame(data).T  # Write in DF and transpose it
df.columns = cols  # Update column names
#print(df)
df.to_csv('/home/cwegescheide/Desktop/Development/Datafiles/TgtFiles/output.csv')
##########################################################################################################################

The Source file:

<?xml version="1.0" encoding="ISO-8859-1"?>
<?xml-stylesheet href="latest_ob.xsl" type="text/xsl"?>
<current_observation version="1.0"
         xmlns:xsd="http://www.w3.org/2001/XMLSchema"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:noNamespaceSchemaLocation="http://www.weather.gov/view/current_observation.xsd">
        <credit>NOAA's National Weather Service</credit>
        <credit_URL>https://weather.gov/</credit_URL>
        <suggested_pickup>15 minutes after the hour</suggested_pickup>
        <suggested_pickup_period>60</suggested_pickup_period>
        <location>Tampa, Tampa International Airport, FL</location>
        <station_id>KTPA</station_id>
        <latitude>27.96139</latitude>
        <longitude>-82.54028</longitude>
        <observation_time>Last Updated on Apr 21 2022, 3:53 am EDT</observation_time>
        <observation_time_rfc822>Thu, 21 Apr 2022 03:53:00 -0400</observation_time_rfc822>
        <weather>Fair</weather>
        <temperature_string>68.0 F (20.0 C)</temperature_string>
        <temp_f>68.0</temp_f>
        <temp_c>20.0</temp_c>
        <relative_humidity>63</relative_humidity>
        <wind_string>Northeast at 6.9 MPH (6 KT)</wind_string>
        <wind_dir>Northeast</wind_dir>
        <wind_degrees>50</wind_degrees>
        <wind_mph>6.9</wind_mph>
        <wind_kt>6</wind_kt>
        <pressure_string>1023.8 mb</pressure_string>
        <pressure_mb>1023.8</pressure_mb>
        <pressure_in>30.23</pressure_in>
        <dewpoint_string>55.0 F (12.8 C)</dewpoint_string>
        <dewpoint_f>55.0</dewpoint_f>
        <dewpoint_c>12.8</dewpoint_c>
        <visibility_mi>10.00</visibility_mi>
        <icon_url_base>https://forecast.weather.gov/images/wtf/small/</icon_url_base>
        <two_day_history_url>https://www.weather.gov/data/obhistory/KTPA.html</two_day_history_url>
        <icon_url_name>nskc.png</icon_url_name>
        <ob_url>https://www.weather.gov/data/METAR/KTPA.1.txt</ob_url>
        <disclaimer_url>https://www.weather.gov/disclaimer.html</disclaimer_url>
        <copyright_url>https://www.weather.gov/disclaimer.html</copyright_url>
        <privacy_policy_url>https://www.weather.gov/notice.html</privacy_policy_url>
</current_observation>



The Output: 

,credit,credit_URL,suggested_pickup,suggested_pickup_period,location,station_id,latitude,longitude,observation_time,observation_time_rfc822,weather,temperature_string,temp_f,temp_c,relative_humidity,wind_string,wind_dir,wind_degrees,wind_mph,wind_kt,pressure_string,pressure_mb,pressure_in,dewpoint_string,dewpoint_f,dewpoint_c,visibility_mi,icon_url_base,two_day_history_url,icon_url_name,ob_url,disclaimer_url,copyright_url,privacy_policy_url
0,NOAA's National Weather Service,[https://weather.gov/,15](https://weather.gov/,15) minutes after the hour,60,"Tampa, Tampa International Airport, FL",KTPA,27.96139,-82.54028,"Last Updated on Apr 21 2022, 3:53 am EDT","Thu, 21 Apr 2022 03:53:00 -0400",Fair,68.0 F (20.0 C),68.0,20.0,63,Northeast at 6.9 MPH (6 KT),Northeast,50,6.9,6,1023.8 mb,1023.8,30.23,55.0 F (12.8 C),55.0,12.8,10.00,[https://forecast.weather.gov/images/wtf/small/,https://www.weather.gov/data/obhistory/KTPA.html,nskc.png,https://www.weather.gov/data/METAR/KTPA.1.txt,https://www.weather.gov/disclaimer.html,https://www.weather.gov/disclaimer.html,https://www.weather.gov/notice.html](https://forecast.weather.gov/images/wtf/small/,https://www.weather.gov/data/obhistory/KTPA.html,nskc.png,https://www.weather.gov/data/METAR/KTPA.1.txt,https://www.weather.gov/disclaimer.html,https://www.weather.gov/disclaimer.html,https://www.weather.gov/notice.html)

Once I figure all this out I will share.    I'm surprised a solution is not easier to find.   I would prefer to only extract the fields that I want and not the entire file.    
I guess this is progress.     I will be sure to check out the Perl solution you shared.    Thank you,  much appreciated.  

Chris

---

### Post by chris53 on 2022-04-26
> **TheFu said:**
> [https://wiki.python.org/moin/RssLibraries](https://wiki.python.org/moin/RssLibraries) seems to have an example for reading the feed.  They don't show a full solution. 

The perl guys show a full solution. They show getting, parsing and printing the different fields.  Basically, to solve the problem above, only the print line would need to be modified. [https://metacpan.org/pod/XML::RSS::Parser::Lite](https://metacpan.org/pod/XML::RSS::Parser::Lite)  I like how the perl guys get to the point, fast.

Definitely like the looks of the script.   I'm gonna give it a shot.    Thanks Fu!  :)

---

### Post by TheFu on 2022-04-26
> **chris53 said:**
> Definitely like the looks of the script.   I'm gonna give it a shot.    Thanks Fu!  :)

Hey!  Didn't you hear, nobody likes perl anymore. Everyone uses Python and they can't wait for Python4!  /s

After all, perl is a "write-once" language. They try to say that nobody, even the original author, can read and modify any perl scripts.  Perl has a different philosophy than Python.  

Python thinks there should be 1-way to accomplish a task and it should work.  

Perl was created by a linguist. Larry thinks that having many ways, each subtly different, to accomplish the same thing is a feature.  It is like the difference in forcing everyone to write to a 3rd grade level stories/poems compared to using their post-Doc PhD writing skills to accomplish amazing things with higher skill and better word selection.  The barrier to entry for perl using "baby perl" is pretty low - not as low as python or php or javascript, but still low.  OTOH, perl in the hands of an expert is freakin' amazing, tight, fast. It takes years to get to a high-intermediate level of perl proficiency.  With perl, we have CPAN (actually metacpan) for both package installs and sharing tested, validated, perl modules.  Just be certain if you ever need to use a specific release of perl or modules tied to that release that you setup virtual perl environments using **perlbrew**.

Python has something for package management and virtual environments, but I've never been able to figure it out, since the pip tool never works with the python I have installed.

I did switch to Ruby for about 5 yrs, but came back to perl when every other year the Ruby guys either replaced ruby or the main libraries, breaking all prior code.  Perl 5.x doesn't do that.  There are minimum versions of perl 5.x needed from time to time, but usually those are 3+ yrs old and your distro already has the perl needed.

---

### Post by #&amp;thj^% on 2022-04-26
> **TheFu said:**
> 

Python has something for package management and virtual environments, but I've never been able to figure it out, since the pip tool never works with the python I have installed.

I'm always impressed by your knowledge, it's kind of a rarity anymore.
Have you looked at this one yet: [https://www.linode.com/docs/guides/how-to-manage-packages-and-virtual-environments-on-linux/](https://www.linode.com/docs/guides/how-to-manage-packages-and-virtual-environments-on-linux/)
> Python is a programming language with a large library of third party modules, or packages. Python developers rely on third party packages to simplify problems when they are writing code. When you install third party Python packages to your machine, you typically use a repository, like Pypi. This repository contains packages that can, by default, be installed with Pip. Pip is a tool used to install Python packages, like Apt for Ubuntu, onto the host system.
but along with you Perl is my go to when possible.

---

