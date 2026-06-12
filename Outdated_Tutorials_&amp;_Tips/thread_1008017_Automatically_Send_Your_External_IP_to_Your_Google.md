---
title: "Automatically Send Your External IP to Your Google Docs"
date: 2008-12-11
forum: Outdated Tutorials &amp; Tips
---

### Post by iQuizzle on 2008-12-11
Dynamic IPs are nice, except that you can never remember what your IP is. This is especially annoying when you are away from home somewhere and you want to SSH or FTP to your home computer. Google documents are a nice place to store information online without having to pay or setup web space. Using this script, you can save your external IP inside the documents section of your gmail account. Then, you will know your home computer's external IP from anywhere just by logging onto gmail and going to the spreadsheet where your IP is stored.

Let's get started!

1) Python will need the google documents api, so go here, download the latest version, unpack and run the install script:

[http://code.google.com/p/gdata-python-client/downloads/list]("http://code.google.com/p/gdata-python-client/downloads/list")

(if you're new to linux commands):
```

wget http://gdata-python-client.googlecode.com/files/gdata.py-1.2.3.tar.gz
tar xvf gdata.py-1.2.3.tar.gz
cd gdata.py-1.2.3/
sudo python setup.py install

```

2) Next, copy this code and paste it into your favorite text editor and save as **googleIP.py**
```

#!/usr/bin/python
#
#
#  1) Install the google documents python api
#  2) Create a spreadsheet in google documents and save it under a name
#     that matches SPREADSHEET_NAME
#  3) Name the column headings of the google spreadsheet 'ip','date','time'
#  4) Edit USERNAME and PASSWD to match your login info
#  5) Make this file executable
#  6) In a terminal window, type 'crontab -e' and add this script to your
#  user's crontab. ex. 56 * * * * /usr/bin/python /path_to_your_script/googleIP.py
#

import os

## Change These to Match Your Info!

SPREADSHEET_NAME = 'MyHomeIP' # google documents spreadsheet name
USERNAME = 'your_username_here' # google/gmail login id
PASSWD = 'your_password_here' # google/gmail login password
BASE_DIR = '/tmp/' # Base Directory to locally save your IP info
                   # trailing slash required!
IP_WEBSITE = 'www.whatismyip.org'
#IP_WEBSITE = 'whatismyip.everdot.org/ip' # alternate website

## Function Definitions

def StringToDictionary(row_data):
  result = {}
  for param in row_data.split():
    name, value = param.split('=')
    result[name] = value
  return result

def load():
  import gdata.spreadsheet.service
  gd_client = gdata.spreadsheet.service.SpreadsheetsService()
  gd_client.email = USERNAME
  gd_client.password = PASSWD
  gd_client.ProgrammaticLogin()
  return gd_client

def updateIP(ip):
  import time,string
  gd_client = load()
  docs= gd_client.GetSpreadsheetsFeed()
  spreads = []
  for i in docs.entry: spreads.append(i.title.text)
  spread_number = None
  for i,j in enumerate(spreads):
    if j == SPREADSHEET_NAME: spread_number = i
  if spread_number == None:
    return 0

  key = docs.entry[spread_number].id.text.rsplit('/', 1)[1]
  feed = gd_client.GetWorksheetsFeed(key)
  wksht_id = feed.entry[0].id.text.rsplit('/', 1)[1]
  feed = gd_client.GetListFeed(key,wksht_id)
  thetime = time.strftime('%I:%M%p')
  thedate = time.strftime('%m/%d/%y')
  entry = gd_client.InsertRow(StringToDictionary('date='+thedate+' time='+thetime+' ip='+ip),key,wksht_id)
  return 1


## Executed Code

if os.path.exists(BASE_DIR+'CheckIP'): os.remove(BASE_DIR+'CheckIP')
os.system('wget '+IP_WEBSITE+' -t 2 --output-document='+BASE_DIR+'CheckIP')
fh2 = open(BASE_DIR+'CheckIP','r')
ip2 = fh2.read()
fh2.close()

if os.path.exists(BASE_DIR+'CurrentIP'):
  fh1 = open(BASE_DIR+'CurrentIP','r')
  ip1 = fh1.read()
  fh1.close()
else:
  ip1 = ''



if ip1 == ip2: pass
else:
  res = updateIP(ip2)
  if res == 0: raise 'Please Create a Spreadsheet named \''+SPREADSHEET_NAME+'\' in googleDocs.'
  else:
    fh = open(BASE_DIR+'CurrentIP','w')
    fh.write(ip2)
    fh.close()


```

Edit the USERNAME and PASSWD to match your gmail login info.
This file can be saved to the directory of your choosing, but for this example lets put it in ~/Documents/

Make the file executable.
```

cd ~/Documents/
chmod +x googleIP.py

```

3) Log onto your gmail account and create a new **spreadsheet**. If you've never done this before, click on 'Documents' at the top of your gmail account, click 'new > spreadsheet'. In the spreadsheet, the first row is where the names of the colums go. Name cells A1,B1 and C1 'ip','date','time'. They can be placed in any order but use all lower case.

The top should look like this:
```

    A    B    C    D    E
1| ip  date  time 
__________________________
2|
3|
4|

```

Save the spreadsheet as '**MyHomeIP**'. (again case matters, this can be changed easily to something different if you want to change SPREADSHEET_NAME in the python script).

At this point you can test that the script works by running
```

python googleIP.py

```

If you look in /tmp you should see the files CurrentIP and CheckIP. Also you can look at your google documents file and see if it sent the information.

4) Now that you know the script is working, make a cron job to check if your IP has changed.

```

crontab -e

```

Add this line to the file
```

# m h  dom mon dow   command
59 * * * * /usr/bin/python /home/your_username/Documents/googleIP.py

```

This will check at the 59th minute of every hour if your IP has changed. If you want to set it to check less frequently, setting the second * to a number 0-23 will cause it to update daily.

I hope this works for you as it has been very useful to me.

---

