---
title: "Python 3 TabError: can't find cause, only used tabs"
date: 2012-08-13
forum: Programming Talk
---

### Post by Superpelican12 on 2012-08-13
I'm currently trying to teach myself Python 3 (reading the book "Beginning Python, using Python 2.6 and Python 3.1" by James Payne) and I'n now at the basic OOP part. As exercise I decided to write my own class. And use as many things I've learned until now in my class to practice. However when I run my script python complains about a TabError at line 41. It says the indentation is wrong and that I mixed spaces and tabs etc. I've read the line of code several times and the lines above and beneath it but really can't find the cause. Here's my source code:
```

import os
import sys

class Car:
 """
 This class represents a car. You can add and read info about it's instances.
 """
 def __init__(self, car_basic_info = {}):
     self.car_basic_info = car_basic_info
     search_engine = "DuckDuckGo"
     self.search_engine = search_engine
     return None
 
 def load_basic_info(self, info_type, info_value):
     if info_type == "Brand":
         self.car_basic_info["Brand"] = info_value
     elif info_type == "Model":
         self.car_basic_info["Model"] = info_value
     elif info_type == "Color":
         self.car_basic_info["Color"] = info_value
     elif info_type == "Model Year":
         self.car_basic_info["Model Year"] = info_value
     else:
         print("Are you sure you entered the right thing?")
         ynin = input("\n If you're really sure type 'yes' and press enter to continue: ")
         if ynin == "yes":
             self.car_basic_info[info_type] = info_value
         else:
             pass
 
 def list_basic_info(self):
     for x in self.car_basic_info.values():
      print(x)
 
 def search_info_on_web(self):
     try:
         self.web_search_text_raw = self.car_basic_info["Brand"] + " " + self.car_basic_info["Model"]
         if search_engine == "Google":
             web_search_text = self.web_search_text_raw.replace(" ", "%20")
             os.system("firefox www.google.com/search?q=%s" % web_search_text)
        elif search_engine == "DuckDuckGo" or "Yahoo" or "Bing":
            web_search_text = self.web_search_text_raw.replace(" ", "+")
            os.system("firefox http://www.%s.com/search?q=%s"% (search_engine.lower, web_search_text))
     except KeyError:
         print("Not enough information avaible to perform a web search! Please enter brand name and model name")
 def set_search_engine(self, search_engine):
     print("Set your search engine by calling this method with as parameter the name of the search engine.")
     if search_engine == "DuckDuckGo":
         print("Search engine set to the DuckDuckGo, the popular alternative search engine. With handy zero-click boxes")
     elif search_engine == "Google":
         print("Search engine set to Google, the most popular search engine with best search results")
     elif search_engine == "Yahoo":
         print("Search engine set to Yahoo, an widely used alternative to Google")
     elif search_egine == "Bing":
         print("Search engine set to Bing, Microsoft's new alternative search engine")
     else:
         print("Error 404, search engine not found! I've never heard of that search engine. \nSorry but this program does not support that search engine :(")

```
Line 41 is:
"elif search_engine == "DuckDuckGo" or "Yahoo" or "Bing":"

Thanks already for spending some of your time to help me out!

---

### Post by spjackson on 2012-08-13
> **Superpelican12 said:**
> Line 41 is:
"elif search_engine == "DuckDuckGo" or "Yahoo" or "Bing":"

Thanks already for spending some of your time to help me out!
You are welcome. That line is indented by 1 space less than the corresponding if.

---

### Post by Superpelican12 on 2012-08-13
Thanks for trying to help me. I couldn't get the indentation right, so I  ended up deleting all the tabs in the script ( :(  ) and using 1 space  as indentation...

EDIT: Would someone mind to review my code? I'm a real beginner so I've to be sure I teach myself good coding habits and a good style ;)
This is one of my first programs (well I actually don't think you can really call it a program ;) )
Here's the latest (and the greatest :D) source code of my "program":
```

import os
import sys

class Car:
 """
 This class represents a car. You can add and read info about it's instances.
 """
 def __init__(self, car_basic_info = {}):
  self.car_basic_info = car_basic_info
  search_engine = "DuckDuckGo"
  self.search_engine = search_engine
  return None

 def load_basic_info(self, info_type, info_value):
  if info_type == "Brand":
   self.car_basic_info["Brand"] = info_value
  elif info_type == "Model":
   self.car_basic_info["Model"] = info_value
  elif info_type == "Color":
   self.car_basic_info["Color"] = info_value
  elif info_type == "Model Year":
   self.car_basic_info["Model Year"] = info_value
  else:
   print("Are you sure you entered the right thing?")
   ynin = input("If you're really sure type 'yes' and press enter to continue: ")
   if ynin == "yes":
    self.car_basic_info[info_type] = info_value
   else:
    pass
 
 def list_basic_info(self):
  for x in self.car_basic_info.values():
   print(x)

 def search_info_on_web(self):
  try:
   self.web_search_text_raw = self.car_basic_info["Brand"] + " " + self.car_basic_info["Model"]
   if self.search_engine == "Google":
    web_search_text = self.web_search_text_raw.replace(" ", "%20")
    os.system("firefox www.google.com/search?q=%s" % web_search_text)
   elif self.search_engine == "DuckDuckGo" or "Yahoo" or "Bing":
    web_search_text = self.web_search_text_raw.replace(" ", "+")
    
    print("firefox http://www.%s.com/search?q=%s" % (self.search_engine.lower(), web_search_text))
    os.system("firefox http://www.%s.com/search?q=%s" % (self.search_engine.lower(), web_search_text))
  except KeyError:
   print("Not enough information avaible to perform a web search! Please enter brand name and model name")
 def set_search_engine(self, search_engine_name):
  if search_engine_name == "DuckDuckGo":
   print("Search engine set to the DuckDuckGo, the popular alternative search engine. With handy zero-click boxes")
   self.search_engine = search_engine_name  
  elif search_engine_name == "Google":
   print("Search engine set to Google, the most popular search engine with best search results")
   self.search_engine = search_engine_name  
  elif search_engine_name == "Yahoo":
   print("Search engine set to Yahoo, an widely used alternative to Google")
   self.search_engine = search_engine_name  
  elif search_engine_name == "Bing":
   print("Search engine set to Bing, Microsoft's new alternative search engine")
   self.search_engine = search_engine_name  
  else:
   print("Error 404, search engine not found! \nSorry but this program does not support that search engine :(")

```

Thanks in advance,

Superpelican

---

### Post by cgroza on 2012-08-14
The function load_basic_info could be written in a way that minimizes code repetition. Something like this:
```

if type_info in ["Brand", "Color", "Year"]:
    self.basic_car_info[type_info] = type_value
else:
    #error handling code

```
This would eliminate the need for those if/elifs and would make it a lot easier to add new attributes.
Also, I would suggest that you indent your code with 4 spaces. That's how most of the Python code is written. Good luck with Python. You won't regret it. :D

---

### Post by Superpelican12 on 2012-08-14
Thanks for the tip! Didn't know that statement yet ("if <my_var> in [my, list]"):wink:. Now also going to use that statement to replace:
```

if search_engine_name == "DuckDuckGo":
   print("Search engine set to the DuckDuckGo, the popular alternative search engine. With handy zero-click boxes")
   self.search_engine = search_engine_name  
  elif search_engine_name == "Google":
   print("Search engine set to Google, the most popular search engine with best search results")
   self.search_engine = search_engine_name  
  elif search_engine_name == "Yahoo":
   print("Search engine set to Yahoo, an widely used alternative to Google")
   self.search_engine = search_engine_name  
  elif search_engine_name == "Bing":
   print("Search engine set to Bing, Microsoft's new alternative search engine")
   self.search_engine = search_engine_name

```
In my "search_info_on_web"-method

All my code is available in public domain BTW. ;)

---

