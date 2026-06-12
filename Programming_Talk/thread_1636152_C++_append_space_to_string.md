---
title: "C++ append space to string"
date: 2010-12-02
forum: Programming Talk
---

### Post by Woody1987 on 2010-12-02
I am trying to append some characters to a string but it is skipping any spaces that it comes across. Why?

```

ifstream configFile("config.txt");
string rssFileLocation;
if(configFile.is_open())
{
    string line;
    while(configFile.good())
    {
        getline(configFile, line);

        if(line.size() != 0 && line.at(0) != '#')
        {				
            if(line.substr(0, 17).compare("RSS_file_location") == 0)
	    {
	        for(unsigned int i = 17; i < line.size(); i++)
		{
		    char c = line.at(i);
		    if(rssFileLocation.size() == 0)
		    {
		        if(c != ' ' && c != '=')
			{
			    stringstream ss;
			    string s;
			    ss << c;
			    ss >> s;
			    rssFileLocation.append(s);
			}
		    }
		    else if(rssFileLocation.size() > 0)
		    {
		        stringstream ss;
			string s;
			ss << c;
			ss >> s;
			if(s.compare(" ") == 0)
			    rssFileLocation.append(" ");
			else
			    rssFileLocation.append(s);
		    }
		}
            }
	}
    }
    configFile.close();
}
```

File Contents:
```

#RSS feed file location. This should contain the url of each feed, one after another, e.g. /home/<username>/feedList.txt
RSS_file_location = /home/matt/temp folder/rssFeeds.txt

```

My Current code reads the RSS_file_location as /home/matt/tempfolder/rssFeeds.txt. It ignores the space between temp and folder.

---

### Post by dwhitney67 on 2010-12-02
Just so you know, the stream object has an operator bool() function that assists in converting the stream object to a bool value when needed.

std::getline() returns the stream object that is supplied as the first parameter, and this too can be converted to a bool value when needed.

For example:
```

ifstream file(filename);

if (file)
{
   std::string line;

   while (getline(file, line))
   {
   }
}

```

As for your question, appending to a string can easily be done using the operator+=() function.  For example:
```

std::string message;
const char  PERIOD = '.';

message += "Hello";
message += " ";
message += "World";
message += PERIOD;

```

I cannot think of any reason to stuff one or more values into a stringstream, and then literally extract them to a string.  Pay attention to the stringstream API... there is a str() method that returns the string.

```

std::stringstream ss;
unsigned int      year = 2011;

ss << "Hello World -- Happy New Year and welcome to " << year << '!';

std::cout << ss.str() << std::endl;

```

---

