---
title: "Anki help?"
date: 2011-10-14
forum: New to Ubuntu
---

### Post by mameshiba on 2011-10-14
Hello there,

I need to learn 1000 kanji by April (ARGH!) and I tried installing Anki to help me practise readings. I visited the website ([http://ankisrs.net/#linux](http://ankisrs.net/#linux)) and as instructed, downloaded the file to my home folder and extracted it. I then ran this as instructed in the README and this is what I got:

> carrie@carrie-laptop:~$ ./anki-1.2.9
bash: ./anki-1.2.9: is a directory

So I tried this instead and this was what I got:

> carrie@carrie-laptop:~$ $ (cd libanki && sudo python setup.py install)
bash: syntax error near unexpected token `cd'
carrie@carrie-laptop:~$ $ sudo python setup.py install
$: command not found
carrie@carrie-laptop:~$ $ anki


So in spite of the advice on the website, I installed Anki through Synaptic, which worked fine, only whenever I try to download any of the flashcard sets I get this error message:

> File is corrupt or not an Anki database. Click help for more info.

Debug info:
Traceback (most recent call last):
  File "/usr/share/anki/ankiqt/ui/main.py", line 696, in loadDeck
    self.deck = DeckStorage.Deck(deckPath)
  File "/usr/share/anki/anki/deck.py", line 2804, in Deck
    deck.rebuildQueue()
  File "/usr/share/anki/anki/deck.py", line 683, in rebuildQueue
    self.checkDue()
  File "/usr/share/anki/anki/deck.py", line 663, in checkDue
    stmt % 0, now=time.time()+self.delay0).rowcount
  File "/usr/share/anki/anki/db.py", line 93, in statement
    return self.execute(text(sql), kwargs)
  File "/usr/share/anki/anki/db.py", line 69, in execute
    x = self._session.execute(*a, **ka)
  File "/usr/lib/pymodules/python2.6/sqlalchemy/orm/session.py", line 753, in execute
    clause, params or {})
  File "/usr/lib/pymodules/python2.6/sqlalchemy/engine/base.py", line 824, in execute
    return Connection.executors[c](self, object, multiparams, params)
  File "/usr/lib/pymodules/python2.6/sqlalchemy/engine/base.py", line 874, in _execute_clauseelement
    return self.__execute_context(context)
  File "/usr/lib/pymodules/python2.6/sqlalchemy/engine/base.py", line 896, in __execute_context
    self._cursor_execute(context.cursor, context.statement, context.parameters[0], context=context)
  File "/usr/lib/pymodules/python2.6/sqlalchemy/engine/base.py", line 950, in _cursor_execute
    self._handle_dbapi_exception(e, statement, parameters, cursor, context)
  File "/usr/lib/pymodules/python2.6/sqlalchemy/engine/base.py", line 931, in _handle_dbapi_exception
    raise exc.DBAPIError.instance(statement, parameters, e, connection_invalidated=is_disconnect)
OperationalError: (OperationalError) no such index: ix_cards_priorityDue u'update cards  indexed by ix_cards_priorityDue set isDue = 1 where type = 0 and isDue = 0 and priority in (1,2,3,4) and combinedDue <= ?' [1318647233.3028159]


... that's not the whole error message; the dialogue box that contained it was long and thin and it wasn't possible to maximize or resize it to read/copy the rest.

I read on the website that you should have the most recent version of ubuntu, but I tried to upgrade (from 11.04) using the instructions here: [http://www.ubuntu.com/download/ubuntu/upgrade](http://www.ubuntu.com/download/ubuntu/upgrade), but my Update Manager is not giving me the option to upgrade, even after I have installed all the most recent updates.

Any thoughts on how I can make it work?

---

### Post by jtarin on 2011-10-14
The website says:> Download Latest Release (1.2.8)

After downloading the file, open a terminal and type "sudo dpkg -i <filename.deb>" to install it. _Ubuntu have made their graphical package manager stricter in the coming 11.4 release, so you may not be able to install the deb using the normal package manager. This will be fixed in a future release._


> Debian and Ubuntu had very broken GUI libraries for a while, so if you encounter crashing problems, please make sure your system is up to date. This means system up to date.....not system upgraded.
I would uninstall everything then download the file allocated on the website and follow instructions for installing as they outlined them.
If you click on the link to download it will be a .deb file there is no need to extract it. You can install by following the command line instructions as outlined on the site.

---

### Post by mameshiba on 2011-10-14
Thank you!

---

### Post by jtarin on 2011-10-14
Any additional help.....please ask.

---

