---
title: "PIDA can't save files"
date: 2007-12-18
forum: Programming Talk
---

### Post by cisforcojo on 2007-12-18
Anyone here use PIDA? I just got it and I LOVE how it looks, but there's a HUGE catch, I can't save anything. Here's the error when I try:

```

Exception type: <type 'exceptions.OSError'>

File /usr/share/pida/pida/services/buffermanager.py, line 246, in _cb
    filename=filename)
  File /usr/share/pida/pida/core/boss.py, line 79, in call_command
    return group.call(commandname=commandname, **kw)
  File /usr/share/pida/pida/core/service.py, line 150, in call
    result = self.__call_command(command, **kw)
  File /usr/share/pida/pida/core/service.py, line 158, in __call_command
    return command(**kw)
  File /usr/share/pida/pida/core/command.py, line 72, in __call__
    return self.__callback(**kw)
  File /usr/share/pida/pida/services/editormanager.py, line 101, in cmd_save_as
    self.editor.call('save_as', filename=filename)
  File /usr/share/pida/pida/core/service.py, line 150, in call
    result = self.__call_command(command, **kw)
  File /usr/share/pida/pida/core/service.py, line 158, in __call_command
    return command(**kw)
  File /usr/share/pida/pida/core/command.py, line 72, in __call__
    return self.__callback(**kw)
  File /usr/share/pida/pida/editors/culebraedit.py, line 330, in cmd_save_as
    if not self._file_op(buf, "save", "save"):
  File /usr/share/pida/pida/editors/culebraedit.py, line 283, in _file_op
    getattr(oper, attr)()
  File /usr/share/pida/pida/utils/culebra/buffers.py, line 389, in save
    fd.close()
  File /usr/share/pida/pida/utils/culebra/buffers.py, line 58, in close
    file_mod = os.stat(self.filename)[stat.ST_MODE]
OSError: [Errno 2] No such file or directory: '/home/cojones/Projects/Programming/Python/SQLiteTest/sqltest.py'

```

I just did a 'sudo apt-get install pida' to install it.

I selected the Culebra text editor, not Gvim.

NOTE: I've never installed Culebra nor did pida install it. Also when looking through the Preferences I get a similar crash. Anyone seen this?

---

