---
title: "Python script error must be integers"
date: 2007-11-14
forum: Programming Talk
---

### Post by empthollow on 2007-11-14
I recently downloaded adesklets and installed the deskicon desklet.  When i start my mail icon which is suppose to tell me how many new messages i have i get error checking mail. Any help would be appreciated.  I managed to debug the mount_icon.py script but python is new to me so i don't know where to start on this one.   the python error in the terminal is:
```

================================================================================
Traceback (most recent call last):
  File "./mail_icon.py", line 57, in update
    s = poplib.__dict__['POP3'+['','_SSL'][self.config['ssl']]](self.config['host'])
TypeError: list indices must be integers
None
================================================================================

```

the deskicon.py script refers to this config file:
```
# -*- coding: ASCII -*-
id0 = {'align': 'left',
 'caption': 'Mail',
 'caption_font': 'VeraBd/14',
 'colour': (0, 0, 0, 255),
 'delay': 1,
 'detail_font': 'VeraBd/12',
 'engine': 'mail_icon',
 'exec': 'evolution',
 'host': 'pop-server.new.rr',
 'icon': 'icons/rox.png',
 'method': 'pop3',
 'password': ' password',
 'ssl': 'False',
 'username': 'username'}

```

It recognizes the engine key because the error refers to this script:
```
#!/usr/bin/env python

"""
mail_icon

this is an icon for an email client, it's almost the
same as exec_icon except it shows under the
caption how many new messages you have

i'm only going to explain properties that might
confuse some people.

method: imap4 or pop3
host: mail server
username: mailbox username
password: mailbox password
ssl: True or False
"""

class mail_icon:
  def __init__(self, config, basedir):
    from os.path import join
    
    key_list = ['icon', 'caption', 'caption_font', 'detail_font', 'colour', 'exec', 'align', 'method', 'host', 'username', 'password', 'ssl']
    self.config = {}
    for key in key_list:
      if config.has_key(key) == False:
        print "Config file not setup properly for this icon type"
        adesklets.quit()
      self.config[key] = config[key]
    
    self.size = -2
    self.icon = Image(join(basedir, self.config['icon']), 0, 0)
    self.caption = Text(self.config['caption'], 0, 0, self.config['colour'],  self.config['caption_font'])
    self.detail = Text('a', 0, 0, self.config['colour'],  self.config['detail_font'])
    
  def update(self):
    
    ## following code from mailer 0.0.7
    ## credit: syfou
    
    try:
      # IMAP4
      #
      if self.config['method']=='imap4':
        import imaplib
        s = imaplib.__dict__['IMAP4'+['','_SSL'][self.config['ssl']]](self.config['host'])
        s.login(self.config['username'],self.config['password'])
        s.select()
        size = len(s.search(None, 'UNSEEN')[1][0].split())
        s.logout()

      # POP3
      #
      if self.config['method']=='pop3':
        import poplib
        s = poplib.__dict__['POP3'+['','_SSL'][self.config['ssl']]](self.config['host'])
        s.user(self.config['username'])
        s.pass_(self.config['password'])
        size = len(s.list()[1])
    except:
      # Exception handling: output a significant printout
      #
      size = -1
      print '='*80
      print traceback.print_exc()
      print '='*80
    
    if self.size == size:
      return False
    else:
      self.size = size
    
    if size == -1:
      det_msg = 'error checking mail'
    elif size == 0:
      det_msg = 'no new mail'
    elif size > 0:
      det_msg = '%s new message(s)' % size
    
    self.detail.__init__(det_msg, self.detail._x, self.detail._y, self.detail._c, self.detail._f)
    if self.config['align'] == 'right':
      w, h = self.dimensions()
      self.icon._x = w - self.icon._w
      self.caption._x = 0
      self.detail._x = 0
    else:
      self.icon._x = 0
      self.caption._x = self.icon._w + 10
      self.detail._x = self.icon._w + 10
    
    y = (self.icon._h/2-((self.caption._f_height+self.detail._f_height)/2))
    self.caption._y = y
    self.detail._y = y + self.caption._f_height
    if self.config['align'] == 'right':
      w, h = self.dimensions()
      self.icon._x = w - self.icon._w
      self.caption._x = 0
      self.detail._x = 0
    elif self.config['align'] == 'bottom':
      w, h = self.dimensions()
      self.icon._x = (w / 2) - (self.icon._w / 2)
      self.caption._x = (w / 2) - (self.caption._f_width / 2)
      self.caption._y = self.icon._h + 5
      self.detail._x = (w / 2) - (self.detail._f_width / 2)
      self.detail._y = self.icon._h + 5 + self.caption._f_height
    elif self.config['align'] == 'top':
      w, h = self.dimensions()
      self.icon._x = (w / 2) - (self.icon._w / 2)
      self.caption._x = (w / 2) - (self.caption._f_width / 2)
      self.detail._x = (w / 2) - (self.detail._f_width / 2)
      self.caption._y = 10
      self.detail._y = 10 + self.caption._f_height
      self.icon._y = self.caption._f_height + self.detail._f_height + 10
    
    return True
  
  def dimensions(self):
    cap_len = self.caption._f_width
    det_len = self.detail._f_width
    th = self.caption._f_height + self.detail._f_height
    
    if self.config['align'] in ('left','right'):
      x = self.icon._w + 10 + max([cap_len, det_len])
      y = max([self.icon._h, th])
    elif self.config['align'] in ('top', 'bottom'):
      x = max([self.icon._w, max([cap_len, det_len])])
      y = self.icon._h + 10 + th
    
    return (x, y)
  
  def render(self):
    self.icon.draw()
    self.caption.draw()
    self.detail.draw()
  
  def action(self, delayed, x, y, button):
    import thread
    if button == 1:
      if x >= self.icon._x and x <= (self.icon._x + self.icon._w) and y >= self.icon._y and y <= (self.icon._y + self.icon._h):
        thread.start_new_thread(system, (self.config['exec'],))
```

---

### Post by geirha on 2007-11-14
> **empthollow said:**
> 
```

 'ssl': 'False',

```


Try with ```
 'ssl': False,
```

---

### Post by empthollow on 2007-11-14
i tried it as you suggested, i also tried 0 with and without quotation marks just for fun.  doing False without quotation marks as you suggested gave me this error.
```
================================================================================Traceback (most recent call last):
  File "./mail_icon.py", line 57, in update
    s = poplib.__dict__['POP3'+['','_SSL'][self.config['ssl']]](self.config['host'])
  File "/usr/lib/python2.4/poplib.py", line 84, in __init__
    for res in socket.getaddrinfo(self.host, self.port, 0, socket.SOCK_STREAM):
gaierror: (-2, 'Name or service not known')
None
================================================================================
```

---

### Post by geirha on 2007-11-14
The hostname you got in your config file looks wrong. ```
$ host pop-server.new.rr
Host pop-server.new.rr not found: 3(NXDOMAIN)

```

EDIT: A quick googling suggests it should be pop-server.new.rr.com ..?

---

### Post by empthollow on 2007-11-14
Sweet, thanks for your input.  changed the server and  False w/o quote fixed it for me!

---

