---
title: "File Formats in Vi"
date: 2010-06-06
forum: Programming Talk
---

### Post by COKEDUDE on 2010-06-06
This is some very useful information. This saves you a lot of future problems. 
> File Formats in Vi

If you happen to use Vi, you can change Vi back and forth between DOS and Unix modes for newlines with a simple command. “:set ff=dos” sets the editor to use DOS newline encoding and will save the file in a DOS-encoded format. “:set ff=unix” sets the editor use Unix newlines and will save the file in a Unix format.

Note that changing the format to dos from unix will always work as expected. This is because any file that contains just LF characters for new lines will be converted to CRLF while lines that already end in CRLF will be left as is.

If your Vi config defaults to a unix format and you open a DOS file, you will see the ^M characters. You can either use the dos2unix conversion utility first or change Vi first to the dos format and then to unix.

If you’d like Vi to default to DOS or Unix formating each time you start a new Vi session, you can add the setting to your ~/.vimrc file. In that file, either add “set ff=dos” or “set ff=unix” depending on your needs. Note the lack of the colon, :, in the .vimrc entries.

For more information on the ff or fileformat setting in Vi, check out the official documentation.
[http://chrisjean.com/2009/03/08/convert-dos-formatted-files-to-unix-format-in-ubuntu-and-centos/](http://chrisjean.com/2009/03/08/convert-dos-formatted-files-to-unix-format-in-ubuntu-and-centos/)

---

