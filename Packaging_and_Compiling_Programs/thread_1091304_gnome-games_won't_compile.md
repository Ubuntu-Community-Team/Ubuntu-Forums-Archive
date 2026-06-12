---
title: "gnome-games won't compile"
date: 2009-03-09
forum: Packaging and Compiling Programs
---

### Post by dodle on 2009-03-09
I think something is wrong with my system, because I've been able to compile gnome-games from source before.  I've been struggling with this for about three days now.  ./configure seems to work fine, here is the output of make:```
GOutputStreamSpliceFlags' was here
/usr/local/include/gio-standalone/gio/goutputstream.h:47: error: redefinition of typedef 'GOutputStream'
/usr/local/include/glib-2.0/gio/giotypes.h:100: error: previous declaration of 'GOutputStream' was here
In file included from /usr/local/include/gio-standalone/gio/gbufferedoutputstream.h:27,
                 from /usr/local/include/glib-2.0/gio/gio.h:33,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gfilteroutputstream.h:38: error: redefinition of typedef 'GFilterOutputStream'
/usr/local/include/glib-2.0/gio/giotypes.h:51: error: previous declaration of 'GFilterOutputStream' was here
In file included from /usr/local/include/glib-2.0/gio/gio.h:33,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gbufferedoutputstream.h:38: error: redefinition of typedef 'GBufferedOutputStream'
/usr/local/include/glib-2.0/gio/giotypes.h:38: error: previous declaration of 'GBufferedOutputStream' was here
In file included from /usr/local/include/glib-2.0/gio/gio.h:36,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gdatainputstream.h:38: error: redefinition of typedef 'GDataInputStream'
/usr/local/include/glib-2.0/gio/giotypes.h:40: error: previous declaration of 'GDataInputStream' was here
/usr/local/include/gio-standalone/gio/gdatainputstream.h:63: error: redeclaration of enumerator 'G_DATA_STREAM_BYTE_ORDER_BIG_ENDIAN'
/usr/local/include/glib-2.0/gio/gioenums.h:61: error: previous definition of 'G_DATA_STREAM_BYTE_ORDER_BIG_ENDIAN' was here
/usr/local/include/gio-standalone/gio/gdatainputstream.h:64: error: redeclaration of enumerator 'G_DATA_STREAM_BYTE_ORDER_LITTLE_ENDIAN'
/usr/local/include/glib-2.0/gio/gioenums.h:62: error: previous definition of 'G_DATA_STREAM_BYTE_ORDER_LITTLE_ENDIAN' was here
/usr/local/include/gio-standalone/gio/gdatainputstream.h:66: error: redeclaration of enumerator 'G_DATA_STREAM_BYTE_ORDER_HOST_ENDIAN'
/usr/local/include/glib-2.0/gio/gioenums.h:64: error: previous definition of 'G_DATA_STREAM_BYTE_ORDER_HOST_ENDIAN' was here
/usr/local/include/gio-standalone/gio/gdatainputstream.h:66: error: conflicting types for 'GDataStreamByteOrder'
/usr/local/include/glib-2.0/gio/gioenums.h:64: error: previous declaration of 'GDataStreamByteOrder' was here
/usr/local/include/gio-standalone/gio/gdatainputstream.h:69: error: redeclaration of enumerator 'G_DATA_STREAM_NEWLINE_TYPE_LF'
/usr/local/include/glib-2.0/gio/gioenums.h:77: error: previous definition of 'G_DATA_STREAM_NEWLINE_TYPE_LF' was here
/usr/local/include/gio-standalone/gio/gdatainputstream.h:70: error: redeclaration of enumerator 'G_DATA_STREAM_NEWLINE_TYPE_CR'
/usr/local/include/glib-2.0/gio/gioenums.h:78: error: previous definition of 'G_DATA_STREAM_NEWLINE_TYPE_CR' was here
/usr/local/include/gio-standalone/gio/gdatainputstream.h:71: error: redeclaration of enumerator 'G_DATA_STREAM_NEWLINE_TYPE_CR_LF'
/usr/local/include/glib-2.0/gio/gioenums.h:79: error: previous definition of 'G_DATA_STREAM_NEWLINE_TYPE_CR_LF' was here
/usr/local/include/gio-standalone/gio/gdatainputstream.h:73: error: redeclaration of enumerator 'G_DATA_STREAM_NEWLINE_TYPE_ANY'
/usr/local/include/glib-2.0/gio/gioenums.h:81: error: previous definition of 'G_DATA_STREAM_NEWLINE_TYPE_ANY' was here
/usr/local/include/gio-standalone/gio/gdatainputstream.h:73: error: conflicting types for 'GDataStreamNewlineType'
/usr/local/include/glib-2.0/gio/gioenums.h:81: error: previous declaration of 'GDataStreamNewlineType' was here
In file included from /usr/local/include/gio-standalone/gio/gfileinfo.h:27,
                 from /usr/local/include/gio-standalone/gio/gfile.h:27,
                 from /usr/local/include/gio-standalone/gio/gvolume.h:27,
                 from /usr/local/include/gio-standalone/gio/gdrive.h:27,
                 from /usr/local/include/glib-2.0/gio/gio.h:38,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gfileattribute.h:31: error: redeclaration of enumerator 'G_FILE_ATTRIBUTE_TYPE_INVALID'
/usr/local/include/glib-2.0/gio/gioenums.h:99: error: previous definition of 'G_FILE_ATTRIBUTE_TYPE_INVALID' was here
/usr/local/include/gio-standalone/gio/gfileattribute.h:32: error: redeclaration of enumerator 'G_FILE_ATTRIBUTE_TYPE_STRING'
/usr/local/include/glib-2.0/gio/gioenums.h:100: error: previous definition of 'G_FILE_ATTRIBUTE_TYPE_STRING' was here
/usr/local/include/gio-standalone/gio/gfileattribute.h:33: error: redeclaration of enumerator 'G_FILE_ATTRIBUTE_TYPE_BYTE_STRING'
/usr/local/include/glib-2.0/gio/gioenums.h:101: error: previous definition of 'G_FILE_ATTRIBUTE_TYPE_BYTE_STRING' was here
/usr/local/include/gio-standalone/gio/gfileattribute.h:34: error: redeclaration of enumerator 'G_FILE_ATTRIBUTE_TYPE_BOOLEAN'
/usr/local/include/glib-2.0/gio/gioenums.h:102: error: previous definition of 'G_FILE_ATTRIBUTE_TYPE_BOOLEAN' was here
/usr/local/include/gio-standalone/gio/gfileattribute.h:35: error: redeclaration of enumerator 'G_FILE_ATTRIBUTE_TYPE_UINT32'
/usr/local/include/glib-2.0/gio/gioenums.h:103: error: previous definition of 'G_FILE_ATTRIBUTE_TYPE_UINT32' was here
/usr/local/include/gio-standalone/gio/gfileattribute.h:36: error: redeclaration of enumerator 'G_FILE_ATTRIBUTE_TYPE_INT32'
/usr/local/include/glib-2.0/gio/gioenums.h:104: error: previous definition of 'G_FILE_ATTRIBUTE_TYPE_INT32' was here
/usr/local/include/gio-standalone/gio/gfileattribute.h:37: error: redeclaration of enumerator 'G_FILE_ATTRIBUTE_TYPE_UINT64'
/usr/local/include/glib-2.0/gio/gioenums.h:105: error: previous definition of 'G_FILE_ATTRIBUTE_TYPE_UINT64' was here
/usr/local/include/gio-standalone/gio/gfileattribute.h:38: error: redeclaration of enumerator 'G_FILE_ATTRIBUTE_TYPE_INT64'
/usr/local/include/glib-2.0/gio/gioenums.h:106: error: previous definition of 'G_FILE_ATTRIBUTE_TYPE_INT64' was here
/usr/local/include/gio-standalone/gio/gfileattribute.h:40: error: redeclaration of enumerator 'G_FILE_ATTRIBUTE_TYPE_OBJECT'
/usr/local/include/glib-2.0/gio/gioenums.h:108: error: previous definition of 'G_FILE_ATTRIBUTE_TYPE_OBJECT' was here
/usr/local/include/gio-standalone/gio/gfileattribute.h:40: error: conflicting types for 'GFileAttributeType'
/usr/local/include/glib-2.0/gio/gioenums.h:108: error: previous declaration of 'GFileAttributeType' was here
/usr/local/include/gio-standalone/gio/gfileattribute.h:50: error: redeclaration of enumerator 'G_FILE_ATTRIBUTE_STATUS_UNSET'
/usr/local/include/glib-2.0/gio/gioenums.h:135: error: previous definition of 'G_FILE_ATTRIBUTE_STATUS_UNSET' was here
/usr/local/include/gio-standalone/gio/gfileattribute.h:51: error: redeclaration of enumerator 'G_FILE_ATTRIBUTE_STATUS_SET'
/usr/local/include/glib-2.0/gio/gioenums.h:136: error: previous definition of 'G_FILE_ATTRIBUTE_STATUS_SET' was here
/usr/local/include/gio-standalone/gio/gfileattribute.h:53: error: redeclaration of enumerator 'G_FILE_ATTRIBUTE_STATUS_ERROR_SETTING'
/usr/local/include/glib-2.0/gio/gioenums.h:138: error: previous definition of 'G_FILE_ATTRIBUTE_STATUS_ERROR_SETTING' was here
/usr/local/include/gio-standalone/gio/gfileattribute.h:53: error: conflicting types for 'GFileAttributeStatus'
/usr/local/include/glib-2.0/gio/gioenums.h:138: error: previous declaration of 'GFileAttributeStatus' was here
/usr/local/include/gio-standalone/gio/gfileattribute.h:76: error: conflicting types for 'GFileAttributeInfo'
/usr/local/include/glib-2.0/gio/giotypes.h:69: error: previous declaration of 'GFileAttributeInfo' was here
/usr/local/include/gio-standalone/gio/gfileattribute.h:81: error: conflicting types for 'GFileAttributeInfoList'
/usr/local/include/glib-2.0/gio/giotypes.h:70: error: previous declaration of 'GFileAttributeInfoList' was here
In file included from /usr/local/include/gio-standalone/gio/gfile.h:27,
                 from /usr/local/include/gio-standalone/gio/gvolume.h:27,
                 from /usr/local/include/gio-standalone/gio/gdrive.h:27,
                 from /usr/local/include/glib-2.0/gio/gio.h:38,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gfileinfo.h:39: error: redefinition of typedef 'GFileInfo'
/usr/local/include/glib-2.0/gio/giotypes.h:61: error: previous declaration of 'GFileInfo' was here
/usr/local/include/gio-standalone/gio/gfileinfo.h:41: error: redefinition of typedef 'GFileAttributeMatcher'
/usr/local/include/glib-2.0/gio/giotypes.h:68: error: previous declaration of 'GFileAttributeMatcher' was here
/usr/local/include/gio-standalone/gio/gfileinfo.h:44: error: redeclaration of enumerator 'G_FILE_TYPE_UNKNOWN'
/usr/local/include/glib-2.0/gio/gioenums.h:242: error: previous definition of 'G_FILE_TYPE_UNKNOWN' was here
/usr/local/include/gio-standalone/gio/gfileinfo.h:45: error: redeclaration of enumerator 'G_FILE_TYPE_REGULAR'
/usr/local/include/glib-2.0/gio/gioenums.h:243: error: previous definition of 'G_FILE_TYPE_REGULAR' was here
/usr/local/include/gio-standalone/gio/gfileinfo.h:46: error: redeclaration of enumerator 'G_FILE_TYPE_DIRECTORY'
/usr/local/include/glib-2.0/gio/gioenums.h:244: error: previous definition of 'G_FILE_TYPE_DIRECTORY' was here
/usr/local/include/gio-standalone/gio/gfileinfo.h:47: error: redeclaration of enumerator 'G_FILE_TYPE_SYMBOLIC_LINK'
/usr/local/include/glib-2.0/gio/gioenums.h:245: error: previous definition of 'G_FILE_TYPE_SYMBOLIC_LINK' was here
/usr/local/include/gio-standalone/gio/gfileinfo.h:48: error: redeclaration of enumerator 'G_FILE_TYPE_SPECIAL'
/usr/local/include/glib-2.0/gio/gioenums.h:246: error: previous definition of 'G_FILE_TYPE_SPECIAL' was here
/usr/local/include/gio-standalone/gio/gfileinfo.h:49: error: redeclaration of enumerator 'G_FILE_TYPE_SHORTCUT'
/usr/local/include/glib-2.0/gio/gioenums.h:247: error: previous definition of 'G_FILE_TYPE_SHORTCUT' was here
/usr/local/include/gio-standalone/gio/gfileinfo.h:51: error: redeclaration of enumerator 'G_FILE_TYPE_MOUNTABLE'
/usr/local/include/glib-2.0/gio/gioenums.h:249: error: previous definition of 'G_FILE_TYPE_MOUNTABLE' was here
/usr/local/include/gio-standalone/gio/gfileinfo.h:51: error: conflicting types for 'GFileType'
/usr/local/include/glib-2.0/gio/gioenums.h:249: error: previous declaration of 'GFileType' was here
In file included from /usr/local/include/gio-standalone/gio/gfile.h:28,
                 from /usr/local/include/gio-standalone/gio/gvolume.h:27,
                 from /usr/local/include/gio-standalone/gio/gdrive.h:27,
                 from /usr/local/include/glib-2.0/gio/gio.h:38,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gfileenumerator.h:43: error: redefinition of typedef 'GFileEnumerator'
/usr/local/include/glib-2.0/gio/giotypes.h:48: error: previous declaration of 'GFileEnumerator' was here
In file included from /usr/local/include/gio-standalone/gio/gfile.h:29,
                 from /usr/local/include/gio-standalone/gio/gvolume.h:27,
                 from /usr/local/include/gio-standalone/gio/gdrive.h:27,
                 from /usr/local/include/glib-2.0/gio/gio.h:38,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gfileinputstream.h:38: error: redefinition of typedef 'GFileInputStream'
/usr/local/include/glib-2.0/gio/giotypes.h:71: error: previous declaration of 'GFileInputStream' was here
In file included from /usr/local/include/gio-standalone/gio/gfile.h:30,
                 from /usr/local/include/gio-standalone/gio/gvolume.h:27,
                 from /usr/local/include/gio-standalone/gio/gdrive.h:27,
                 from /usr/local/include/glib-2.0/gio/gio.h:38,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gfileoutputstream.h:38: error: redefinition of typedef 'GFileOutputStream'
/usr/local/include/glib-2.0/gio/giotypes.h:72: error: previous declaration of 'GFileOutputStream' was here
In file included from /usr/local/include/gio-standalone/gio/gfile.h:31,
                 from /usr/local/include/gio-standalone/gio/gvolume.h:27,
                 from /usr/local/include/gio-standalone/gio/gdrive.h:27,
                 from /usr/local/include/glib-2.0/gio/gio.h:38,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gmountoperation.h:39: error: redefinition of typedef 'GMountOperation'
/usr/local/include/glib-2.0/gio/giotypes.h:99: error: previous declaration of 'GMountOperation' was here
/usr/local/include/gio-standalone/gio/gmountoperation.h:59: error: redeclaration of enumerator 'G_PASSWORD_SAVE_NEVER'
/usr/local/include/glib-2.0/gio/gioenums.h:402: error: previous definition of 'G_PASSWORD_SAVE_NEVER' was here
/usr/local/include/gio-standalone/gio/gmountoperation.h:60: error: redeclaration of enumerator 'G_PASSWORD_SAVE_FOR_SESSION'
/usr/local/include/glib-2.0/gio/gioenums.h:403: error: previous definition of 'G_PASSWORD_SAVE_FOR_SESSION' was here
/usr/local/include/gio-standalone/gio/gmountoperation.h:62: error: redeclaration of enumerator 'G_PASSWORD_SAVE_PERMANENTLY'
/usr/local/include/glib-2.0/gio/gioenums.h:405: error: previous definition of 'G_PASSWORD_SAVE_PERMANENTLY' was here
/usr/local/include/gio-standalone/gio/gmountoperation.h:62: error: conflicting types for 'GPasswordSave'
/usr/local/include/glib-2.0/gio/gioenums.h:405: error: previous declaration of 'GPasswordSave' was here
In file included from /usr/local/include/gio-standalone/gio/gvolume.h:27,
                 from /usr/local/include/gio-standalone/gio/gdrive.h:27,
                 from /usr/local/include/glib-2.0/gio/gio.h:38,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gfile.h:42: error: redeclaration of enumerator 'G_FILE_QUERY_INFO_NOFOLLOW_SYMLINKS'
/usr/local/include/glib-2.0/gio/gioenums.h:151: error: previous definition of 'G_FILE_QUERY_INFO_NOFOLLOW_SYMLINKS' was here
/usr/local/include/gio-standalone/gio/gfile.h:42: error: conflicting types for 'GFileQueryInfoFlags'
/usr/local/include/glib-2.0/gio/gioenums.h:151: error: previous declaration of 'GFileQueryInfoFlags' was here
/usr/local/include/gio-standalone/gio/gfile.h:47: error: conflicting types for 'GFileCreateFlags'
/usr/local/include/glib-2.0/gio/gioenums.h:165: error: previous declaration of 'GFileCreateFlags' was here
/usr/local/include/gio-standalone/gio/gfile.h:50: error: redeclaration of enumerator 'G_FILE_COPY_OVERWRITE'
/usr/local/include/glib-2.0/gio/gioenums.h:206: error: previous definition of 'G_FILE_COPY_OVERWRITE' was here
/usr/local/include/gio-standalone/gio/gfile.h:51: error: redeclaration of enumerator 'G_FILE_COPY_BACKUP'
/usr/local/include/glib-2.0/gio/gioenums.h:207: error: previous definition of 'G_FILE_COPY_BACKUP' was here
/usr/local/include/gio-standalone/gio/gfile.h:52: error: redeclaration of enumerator 'G_FILE_COPY_NOFOLLOW_SYMLINKS'
/usr/local/include/glib-2.0/gio/gioenums.h:208: error: previous definition of 'G_FILE_COPY_NOFOLLOW_SYMLINKS' was here
/usr/local/include/gio-standalone/gio/gfile.h:54: error: redeclaration of enumerator 'G_FILE_COPY_ALL_METADATA'
/usr/local/include/glib-2.0/gio/gioenums.h:209: error: previous definition of 'G_FILE_COPY_ALL_METADATA' was here
/usr/local/include/gio-standalone/gio/gfile.h:54: error: conflicting types for 'GFileCopyFlags'
/usr/local/include/glib-2.0/gio/gioenums.h:211: error: previous declaration of 'GFileCopyFlags' was here
/usr/local/include/gio-standalone/gio/gfile.h:59: error: conflicting types for 'GFileMonitorFlags'
/usr/local/include/glib-2.0/gio/gioenums.h:224: error: previous declaration of 'GFileMonitorFlags' was here
/usr/local/include/gio-standalone/gio/gfile.h:61: error: redefinition of typedef 'GFile'
/usr/local/include/glib-2.0/gio/giotypes.h:60: error: previous declaration of 'GFile' was here
/usr/local/include/gio-standalone/gio/gfile.h:64: error: redefinition of typedef 'GFileMonitor'
/usr/local/include/glib-2.0/gio/giotypes.h:49: error: previous declaration of 'GFileMonitor' was here
/usr/local/include/gio-standalone/gio/gfile.h:65: error: redefinition of typedef 'GVolume'
/usr/local/include/glib-2.0/gio/giotypes.h:111: error: previous declaration of 'GVolume' was here
/usr/local/include/gio-standalone/gio/gfile.h:67: error: redefinition of typedef 'GFileProgressCallback'
/usr/local/include/glib-2.0/gio/giotypes.h:137: error: previous declaration of 'GFileProgressCallback' was here
/usr/local/include/gio-standalone/gio/gfile.h:70: error: redefinition of typedef 'GFileReadMoreCallback'
/usr/local/include/glib-2.0/gio/giotypes.h:154: error: previous declaration of 'GFileReadMoreCallback' was here
In file included from /usr/local/include/gio-standalone/gio/gdrive.h:27,
                 from /usr/local/include/glib-2.0/gio/gio.h:38,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gvolume.h:37: error: redefinition of typedef 'GDrive'
/usr/local/include/glib-2.0/gio/giotypes.h:47: error: previous declaration of 'GDrive' was here
In file included from /usr/local/include/gio-standalone/gio/gfileicon.h:26,
                 from /usr/local/include/glib-2.0/gio/gio.h:43,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gloadableicon.h:37: error: redefinition of typedef 'GLoadableIcon'
/usr/local/include/glib-2.0/gio/giotypes.h:89: error: previous declaration of 'GLoadableIcon' was here
In file included from /usr/local/include/glib-2.0/gio/gio.h:43,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gfileicon.h:38: error: redefinition of typedef 'GFileIcon'
/usr/local/include/glib-2.0/gio/giotypes.h:73: error: previous declaration of 'GFileIcon' was here
In file included from /usr/local/include/glib-2.0/gio/gio.h:46,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gfilemonitor.h:39: error: redeclaration of enumerator 'G_FILE_MONITOR_EVENT_CHANGED'
/usr/local/include/glib-2.0/gio/gioenums.h:282: error: previous definition of 'G_FILE_MONITOR_EVENT_CHANGED' was here
/usr/local/include/gio-standalone/gio/gfilemonitor.h:40: error: redeclaration of enumerator 'G_FILE_MONITOR_EVENT_CHANGES_DONE_HINT'
/usr/local/include/glib-2.0/gio/gioenums.h:283: error: previous definition of 'G_FILE_MONITOR_EVENT_CHANGES_DONE_HINT' was here
/usr/local/include/gio-standalone/gio/gfilemonitor.h:41: error: redeclaration of enumerator 'G_FILE_MONITOR_EVENT_DELETED'
/usr/local/include/glib-2.0/gio/gioenums.h:284: error: previous definition of 'G_FILE_MONITOR_EVENT_DELETED' was here
/usr/local/include/gio-standalone/gio/gfilemonitor.h:42: error: redeclaration of enumerator 'G_FILE_MONITOR_EVENT_CREATED'
/usr/local/include/glib-2.0/gio/gioenums.h:285: error: previous definition of 'G_FILE_MONITOR_EVENT_CREATED' was here
/usr/local/include/gio-standalone/gio/gfilemonitor.h:43: error: redeclaration of enumerator 'G_FILE_MONITOR_EVENT_ATTRIBUTE_CHANGED'
/usr/local/include/glib-2.0/gio/gioenums.h:286: error: previous definition of 'G_FILE_MONITOR_EVENT_ATTRIBUTE_CHANGED' was here
/usr/local/include/gio-standalone/gio/gfilemonitor.h:44: error: redeclaration of enumerator 'G_FILE_MONITOR_EVENT_PRE_UNMOUNT'
/usr/local/include/glib-2.0/gio/gioenums.h:287: error: previous definition of 'G_FILE_MONITOR_EVENT_PRE_UNMOUNT' was here
/usr/local/include/gio-standalone/gio/gfilemonitor.h:46: error: redeclaration of enumerator 'G_FILE_MONITOR_EVENT_UNMOUNTED'
/usr/local/include/glib-2.0/gio/gioenums.h:289: error: previous definition of 'G_FILE_MONITOR_EVENT_UNMOUNTED' was here
/usr/local/include/gio-standalone/gio/gfilemonitor.h:46: error: conflicting types for 'GFileMonitorEvent'
/usr/local/include/glib-2.0/gio/gioenums.h:289: error: previous declaration of 'GFileMonitorEvent' was here
In file included from /usr/local/include/glib-2.0/gio/gio.h:47,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gfilenamecompleter.h:37: error: redefinition of typedef 'GFilenameCompleter'
/usr/local/include/glib-2.0/gio/giotypes.h:74: error: previous declaration of 'GFilenameCompleter' was here
In file included from /usr/local/include/glib-2.0/gio/gio.h:56,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/giomodule.h:38: error: redefinition of typedef 'GIOModule'
/usr/local/include/glib-2.0/gio/giotypes.h:79: error: previous declaration of 'GIOModule' was here
In file included from /usr/local/include/glib-2.0/gio/gio.h:59,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gmemoryinputstream.h:38: error: redefinition of typedef 'GMemoryInputStream'
/usr/local/include/glib-2.0/gio/giotypes.h:90: error: previous declaration of 'GMemoryInputStream' was here
In file included from /usr/local/include/glib-2.0/gio/gio.h:60,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gmemoryoutputstream.h:38: error: redefinition of typedef 'GMemoryOutputStream'
/usr/local/include/glib-2.0/gio/giotypes.h:91: error: previous declaration of 'GMemoryOutputStream' was here
In file included from /usr/local/include/glib-2.0/gio/gnativevolumemonitor.h:4,
                 from /usr/local/include/glib-2.0/gio/gio.h:63,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gvolumemonitor.h:39: error: redefinition of typedef 'GVolumeMonitor'
/usr/local/include/glib-2.0/gio/giotypes.h:112: error: previous declaration of 'GVolumeMonitor' was here
In file included from /usr/local/include/glib-2.0/gio/gio.h:65,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gseekable.h:36: error: redefinition of typedef 'GSeekable'
/usr/local/include/glib-2.0/gio/giotypes.h:101: error: previous declaration of 'GSeekable' was here
In file included from /usr/local/include/glib-2.0/gio/gio.h:66,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gsimpleasyncresult.h:38: error: redefinition of typedef 'GSimpleAsyncResult'
/usr/local/include/glib-2.0/gio/giotypes.h:102: error: previous declaration of 'GSimpleAsyncResult' was here
/usr/local/include/gio-standalone/gio/gsimpleasyncresult.h:41: error: redefinition of typedef 'GSimpleAsyncThreadFunc'
/usr/local/include/glib-2.0/gio/giotypes.h:190: error: previous declaration of 'GSimpleAsyncThreadFunc' was here
In file included from /usr/local/include/glib-2.0/gio/gio.h:67,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gthemedicon.h:37: error: redefinition of typedef 'GThemedIcon'
/usr/local/include/glib-2.0/gio/giotypes.h:103: error: previous declaration of 'GThemedIcon' was here
In file included from /usr/local/include/glib-2.0/gio/gio.h:68,
                 from /usr/include/gtk-2.0/gdk/gdkapplaunchcontext.h:30,
                 from /usr/include/gtk-2.0/gdk/gdk.h:32,
                 from /usr/include/gtk-2.0/gtk/gtklabel.h:34,
                 from games-clock.h:15,
                 from games-clock.c:13:
/usr/local/include/gio-standalone/gio/gvfs.h:38: error: redefinition of typedef 'GVfs'
/usr/local/include/glib-2.0/gio/giotypes.h:104: error: previous declaration of 'GVfs' was here
make[2]: *** [games-clock.lo] Error 1
make[2]: Leaving directory `/home/jordan/Desktop/gnome-games-2.6.2/libgames-support'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jordan/Desktop/gnome-games-2.6.2'
make: *** [all] Error 2

```Here is the config.log:```
This file contains any messages produced by compilers while
running configure, to aid debugging if configure makes a mistake.

It was created by gnome-games configure 2.6.2, which was
generated by GNU Autoconf 2.57.  Invocation command line was

  $ ./configure --prefix=/home/jordan/Desktop/gnome-games-win32

## --------- ##
## Platform. ##
## --------- ##

hostname = irwin-laptop
uname -m = i686
uname -r = 2.6.24-23-generic
uname -s = Linux
uname -v = #1 SMP Mon Jan 26 00:13:11 UTC 2009

/usr/bin/uname -p = unknown
/bin/uname -X     = unknown

/bin/arch              = unknown
/usr/bin/arch -k       = unknown
/usr/convex/getsysinfo = unknown
hostinfo               = unknown
/bin/machine           = unknown
/usr/bin/oslevel       = unknown
/bin/universe          = unknown

PATH: /usr/local/sbin
PATH: /usr/local/bin
PATH: /usr/sbin
PATH: /usr/bin
PATH: /sbin
PATH: /bin
PATH: /usr/games


## ----------- ##
## Core tests. ##
## ----------- ##

configure:1529: checking for a BSD-compatible install
configure:1583: result: /usr/bin/install -c
configure:1594: checking whether build environment is sane
configure:1637: result: yes
configure:1670: checking for gawk
configure:1686: found /usr/bin/gawk
configure:1696: result: gawk
configure:1706: checking whether make sets $(MAKE)
configure:1726: result: yes
configure:1893: checking whether to enable maintainer-specific portions of Makefiles
configure:1902: result: no
configure:1965: checking for gcc
configure:1981: found /usr/bin/gcc
configure:1991: result: gcc
configure:2235: checking for C compiler version
configure:2238: gcc --version </dev/null >&5
gcc (Ubuntu 4.3.2-1ubuntu11) 4.3.2
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:2241: $? = 0
configure:2243: gcc -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.2-1ubuntu11' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) 
configure:2246: $? = 0
configure:2248: gcc -V </dev/null >&5
gcc: '-V' option must have argument
configure:2251: $? = 1
configure:2275: checking for C compiler default output
configure:2278: gcc    conftest.c  >&5
configure:2281: $? = 0
configure:2327: result: a.out
configure:2332: checking whether the C compiler works
configure:2338: ./a.out
configure:2341: $? = 0
configure:2358: result: yes
configure:2365: checking whether we are cross compiling
configure:2367: result: no
configure:2370: checking for suffix of executables
configure:2372: gcc -o conftest    conftest.c  >&5
configure:2375: $? = 0
configure:2400: result: 
configure:2406: checking for suffix of object files
configure:2428: gcc -c   conftest.c >&5
configure:2431: $? = 0
configure:2453: result: o
configure:2457: checking whether we are using the GNU C compiler
configure:2482: gcc -c   conftest.c >&5
configure:2485: $? = 0
configure:2488: test -s conftest.o
configure:2491: $? = 0
configure:2504: result: yes
configure:2510: checking whether gcc accepts -g
configure:2532: gcc -c -g  conftest.c >&5
configure:2535: $? = 0
configure:2538: test -s conftest.o
configure:2541: $? = 0
configure:2552: result: yes
configure:2569: checking for gcc option to accept ANSI C
configure:2630: gcc  -c -g -O2  conftest.c >&5
configure:2633: $? = 0
configure:2636: test -s conftest.o
configure:2639: $? = 0
configure:2657: result: none needed
configure:2675: gcc -c -g -O2  conftest.c >&5
conftest.c:2: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'me'
configure:2678: $? = 1
configure: failed program was:
| #ifndef __cplusplus
|   choke me
| #endif
configure:2798: checking for style of include used by make
configure:2826: result: GNU
configure:2854: checking dependency style of gcc
configure:2937: result: gcc3
configure:2959: checking how to run the C preprocessor
configure:2995: gcc -E  conftest.c
configure:3001: $? = 0
configure:3033: gcc -E  conftest.c
configure:3034:28: error: ac_nonexistent.h: No such file or directory
configure:3039: $? = 1
configure: failed program was:
| #line 3024 "configure"
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "gnome-games"
| #define PACKAGE_TARNAME "gnome-games"
| #define PACKAGE_VERSION "2.6.2"
| #define PACKAGE_STRING "gnome-games 2.6.2"
| #define PACKAGE_BUGREPORT "http://bugzilla.gnome.org/enter_bug.cgi?product=gnome-games"
| #define PACKAGE "gnome-games"
| #define VERSION "2.6.2"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:3077: result: gcc -E
configure:3102: gcc -E  conftest.c
configure:3108: $? = 0
configure:3140: gcc -E  conftest.c
configure:3141:28: error: ac_nonexistent.h: No such file or directory
configure:3146: $? = 1
configure: failed program was:
| #line 3131 "configure"
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "gnome-games"
| #define PACKAGE_TARNAME "gnome-games"
| #define PACKAGE_VERSION "2.6.2"
| #define PACKAGE_STRING "gnome-games 2.6.2"
| #define PACKAGE_BUGREPORT "http://bugzilla.gnome.org/enter_bug.cgi?product=gnome-games"
| #define PACKAGE "gnome-games"
| #define VERSION "2.6.2"
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:3240: checking for g++
configure:3256: found /usr/bin/g++
configure:3266: result: g++
configure:3282: checking for C++ compiler version
configure:3285: g++ --version </dev/null >&5
g++ (Ubuntu 4.3.2-1ubuntu11) 4.3.2
Copyright (C) 2008 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

configure:3288: $? = 0
configure:3290: g++ -v </dev/null >&5
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --with-pkgversion='Ubuntu 4.3.2-1ubuntu11' --with-bugurl=file:///usr/share/doc/gcc-4.3/README.Bugs --enable-languages=c,c++,fortran,objc,obj-c++ --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --with-gxx-include-dir=/usr/include/c++/4.3 --program-suffix=-4.3 --enable-clocale=gnu --enable-libstdcxx-debug --enable-objc-gc --enable-mpfr --enable-targets=all --enable-checking=release --build=i486-linux-gnu --host=i486-linux-gnu --target=i486-linux-gnu
Thread model: posix
gcc version 4.3.2 (Ubuntu 4.3.2-1ubuntu11) 
configure:3293: $? = 0
configure:3295: g++ -V </dev/null >&5
g++: '-V' option must have argument
configure:3298: $? = 1
configure:3301: checking whether we are using the GNU C++ compiler
configure:3326: g++ -c   conftest.cc >&5
configure:3329: $? = 0
configure:3332: test -s conftest.o
configure:3335: $? = 0
configure:3348: result: yes
configure:3354: checking whether g++ accepts -g
configure:3376: g++ -c -g  conftest.cc >&5
configure:3379: $? = 0
configure:3382: test -s conftest.o
configure:3385: $? = 0
configure:3396: result: yes
configure:3440: g++ -c -g -O2  conftest.cc >&5
configure:3443: $? = 0
configure:3446: test -s conftest.o
configure:3449: $? = 0
configure:3476: g++ -c -g -O2  conftest.cc >&5
configure: In function 'int main()':
configure:3473: error: 'exit' was not declared in this scope
configure:3479: $? = 1
configure: failed program was:
| #line 3459 "configure"
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "gnome-games"
| #define PACKAGE_TARNAME "gnome-games"
| #define PACKAGE_VERSION "2.6.2"
| #define PACKAGE_STRING "gnome-games 2.6.2"
| #define PACKAGE_BUGREPORT "http://bugzilla.gnome.org/enter_bug.cgi?product=gnome-games"
| #define PACKAGE "gnome-games"
| #define VERSION "2.6.2"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| exit (42);
|   ;
|   return 0;
| }
configure:3440: g++ -c -g -O2  conftest.cc >&5
configure:3443: $? = 0
configure:3446: test -s conftest.o
configure:3449: $? = 0
configure:3476: g++ -c -g -O2  conftest.cc >&5
configure:3479: $? = 0
configure:3482: test -s conftest.o
configure:3485: $? = 0
configure:3510: checking dependency style of g++
configure:3593: result: gcc3
configure:3613: checking for intltool >= 0.29
configure:3623: result: 0.30 found
configure:3678: checking for perl
configure:3696: found /usr/bin/perl
configure:3708: result: /usr/bin/perl
configure:3825: checking build system type
configure:3843: result: i686-pc-linux-gnu
configure:3851: checking host system type
configure:3865: result: i686-pc-linux-gnu
configure:3873: checking for a sed that does not truncate output
configure:3927: result: /bin/sed
configure:3930: checking for egrep
configure:3940: result: grep -E
configure:3956: checking for ld used by gcc
configure:4023: result: /usr/bin/ld
configure:4032: checking if the linker (/usr/bin/ld) is GNU ld
configure:4047: result: yes
configure:4052: checking for /usr/bin/ld option to reload object files
configure:4059: result: -r
configure:4068: checking for BSD-compatible nm
configure:4110: result: /usr/bin/nm -B
configure:4114: checking whether ln -s works
configure:4118: result: yes
configure:4125: checking how to recognise dependent libraries
configure:4308: result: pass_all
configure:4508: checking for ANSI C header files
configure:4534: gcc -c -g -O2  conftest.c >&5
configure:4537: $? = 0
configure:4540: test -s conftest.o
configure:4543: $? = 0
configure:4635: gcc -o conftest -g -O2   conftest.c  >&5
configure: In function 'main':
configure:4633: warning: incompatible implicit declaration of built-in function 'exit'
configure:4638: $? = 0
configure:4640: ./conftest
configure:4643: $? = 0
configure:4658: result: yes
configure:4682: checking for sys/types.h
configure:4699: gcc -c -g -O2  conftest.c >&5
configure:4702: $? = 0
configure:4705: test -s conftest.o
configure:4708: $? = 0
configure:4719: result: yes
configure:4682: checking for sys/stat.h
configure:4699: gcc -c -g -O2  conftest.c >&5
configure:4702: $? = 0
configure:4705: test -s conftest.o
configure:4708: $? = 0
configure:4719: result: yes
configure:4682: checking for stdlib.h
configure:4699: gcc -c -g -O2  conftest.c >&5
configure:4702: $? = 0
configure:4705: test -s conftest.o
configure:4708: $? = 0
configure:4719: result: yes
configure:4682: checking for string.h
configure:4699: gcc -c -g -O2  conftest.c >&5
configure:4702: $? = 0
configure:4705: test -s conftest.o
configure:4708: $? = 0
configure:4719: result: yes
configure:4682: checking for memory.h
configure:4699: gcc -c -g -O2  conftest.c >&5
configure:4702: $? = 0
configure:4705: test -s conftest.o
configure:4708: $? = 0
configure:4719: result: yes
configure:4682: checking for strings.h
configure:4699: gcc -c -g -O2  conftest.c >&5
configure:4702: $? = 0
configure:4705: test -s conftest.o
configure:4708: $? = 0
configure:4719: result: yes
configure:4682: checking for inttypes.h
configure:4699: gcc -c -g -O2  conftest.c >&5
configure:4702: $? = 0
configure:4705: test -s conftest.o
configure:4708: $? = 0
configure:4719: result: yes
configure:4682: checking for stdint.h
configure:4699: gcc -c -g -O2  conftest.c >&5
configure:4702: $? = 0
configure:4705: test -s conftest.o
configure:4708: $? = 0
configure:4719: result: yes
configure:4682: checking for unistd.h
configure:4699: gcc -c -g -O2  conftest.c >&5
configure:4702: $? = 0
configure:4705: test -s conftest.o
configure:4708: $? = 0
configure:4719: result: yes
configure:4745: checking dlfcn.h usability
configure:4758: gcc -c -g -O2  conftest.c >&5
configure:4761: $? = 0
configure:4764: test -s conftest.o
configure:4767: $? = 0
configure:4777: result: yes
configure:4781: checking dlfcn.h presence
configure:4792: gcc -E  conftest.c
configure:4798: $? = 0
configure:4817: result: yes
configure:4853: checking for dlfcn.h
configure:4860: result: yes
configure:4878: checking how to run the C++ preprocessor
configure:4910: g++ -E  conftest.cc
configure:4916: $? = 0
configure:4948: g++ -E  conftest.cc
configure:4963:28: error: ac_nonexistent.h: No such file or directory
configure:4954: $? = 1
configure: failed program was:
| #line 4939 "configure"
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "gnome-games"
| #define PACKAGE_TARNAME "gnome-games"
| #define PACKAGE_VERSION "2.6.2"
| #define PACKAGE_STRING "gnome-games 2.6.2"
| #define PACKAGE_BUGREPORT "http://bugzilla.gnome.org/enter_bug.cgi?product=gnome-games"
| #define PACKAGE "gnome-games"
| #define VERSION "2.6.2"
| #ifdef __cplusplus
| #include <stdlib.h>
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:4992: result: g++ -E
configure:5017: g++ -E  conftest.cc
configure:5023: $? = 0
configure:5055: g++ -E  conftest.cc
configure:5070:28: error: ac_nonexistent.h: No such file or directory
configure:5061: $? = 1
configure: failed program was:
| #line 5046 "configure"
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "gnome-games"
| #define PACKAGE_TARNAME "gnome-games"
| #define PACKAGE_VERSION "2.6.2"
| #define PACKAGE_STRING "gnome-games 2.6.2"
| #define PACKAGE_BUGREPORT "http://bugzilla.gnome.org/enter_bug.cgi?product=gnome-games"
| #define PACKAGE "gnome-games"
| #define VERSION "2.6.2"
| #ifdef __cplusplus
| #include <stdlib.h>
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| /* end confdefs.h.  */
| #include <ac_nonexistent.h>
configure:5155: checking for g77
configure:5184: result: no
configure:5155: checking for f77
configure:5184: result: no
configure:5155: checking for xlf
configure:5184: result: no
configure:5155: checking for frt
configure:5184: result: no
configure:5155: checking for pgf77
configure:5184: result: no
configure:5155: checking for fl32
configure:5184: result: no
configure:5155: checking for af77
configure:5184: result: no
configure:5155: checking for fort77
configure:5184: result: no
configure:5155: checking for f90
configure:5184: result: no
configure:5155: checking for xlf90
configure:5184: result: no
configure:5155: checking for pgf90
configure:5184: result: no
configure:5155: checking for epcf90
configure:5184: result: no
configure:5155: checking for f95
configure:5184: result: no
configure:5155: checking for fort
configure:5184: result: no
configure:5155: checking for xlf95
configure:5184: result: no
configure:5155: checking for lf95
configure:5184: result: no
configure:5155: checking for g95
configure:5184: result: no
configure:5196: checking for Fortran 77 compiler version
configure:5199:  --version </dev/null >&5
./configure: line 5200: --version: command not found
configure:5202: $? = 127
configure:5204:  -v </dev/null >&5
./configure: line 5205: -v: command not found
configure:5207: $? = 127
configure:5209:  -V </dev/null >&5
./configure: line 5210: -V: command not found
configure:5212: $? = 127
configure:5219: checking whether we are using the GNU Fortran 77 compiler
configure:5233:  -c  conftest.F >&5
./configure: line 5234: -c: command not found
configure:5236: $? = 127
configure: failed program was:
|       program main
| #ifndef __GNUC__
|        choke me
| #endif
| 
|       end
configure:5255: result: no
configure:5262: checking whether  accepts -g
configure:5274:  -c -g conftest.f >&5
./configure: line 5275: -c: command not found
configure:5277: $? = 127
configure: failed program was:
|       program main
| 
|       end
configure:5295: result: no
configure:5323: checking the maximum length of command line arguments
configure:5388: result: 32768
configure:5399: checking command to parse /usr/bin/nm -B output from gcc object
configure:5488: gcc -c -g -O2  conftest.c >&5
configure:5491: $? = 0
configure:5495: /usr/bin/nm -B conftest.o \| sed -n -e 's/^.*[ 	]\([ABCDGIRSTW][ABCDGIRSTW]*\)[ 	][ 	]*\(\)\([_A-Za-z][_A-Za-z0-9]*\)$/\1 \2\3 \3/p' \> conftest.nm
configure:5498: $? = 0
configure:5550: gcc -o conftest -g -O2   conftest.c conftstm.o >&5
configure:5553: $? = 0
configure:5591: result: ok
configure:5595: checking for objdir
configure:5610: result: .libs
configure:5700: checking for ar
configure:5716: found /usr/bin/ar
configure:5727: result: ar
configure:5780: checking for ranlib
configure:5796: found /usr/bin/ranlib
configure:5807: result: ranlib
configure:5860: checking for strip
configure:5876: found /usr/bin/strip
configure:5887: result: strip
configure:6149: checking if gcc static flag  works
configure:6172: result: yes
configure:6190: checking if gcc supports -fno-rtti -fno-exceptions
configure:6208: gcc -c -g -O2  -fno-rtti -fno-exceptions conftest.c >&5
cc1: warning: command line option "-fno-rtti" is valid for C++/ObjC++ but not for C
configure:6212: $? = 0
configure:6223: result: no
configure:6238: checking for gcc option to produce PIC
configure:6415: result: -fPIC
configure:6423: checking if gcc PIC flag -fPIC works
configure:6441: gcc -c -g -O2  -fPIC -DPIC conftest.c >&5
configure:6445: $? = 0
configure:6456: result: yes
configure:6480: checking if gcc supports -c -o file.o
configure:6501: gcc -c -g -O2  -o out/conftest2.o conftest.c >&5
configure:6505: $? = 0
configure:6525: result: yes
configure:6551: checking whether the gcc linker (/usr/bin/ld) supports shared libraries
configure:7379: result: yes
configure:7405: checking whether -lc should be explicitly linked in
configure:7410: gcc -c -g -O2  conftest.c >&5
configure:7413: $? = 0
configure:7427: gcc -shared conftest.o  -v -Wl,-soname -Wl,conftest -o conftest 2\>\&1 \| grep  -lc  \>/dev/null 2\>\&1
configure:7430: $? = 0
configure:7442: result: no
configure:7450: checking dynamic linker characteristics
configure:7990: result: GNU/Linux ld.so
configure:7994: checking how to hardcode library paths into programs
configure:8019: result: immediate
configure:8033: checking whether stripping libraries is possible
configure:8038: result: yes
configure:8782: checking if libtool supports shared libraries
configure:8784: result: yes
configure:8787: checking whether to build shared libraries
configure:8845: result: yes
configure:8848: checking whether to build static libraries
configure:8852: result: yes
configure:8944: creating libtool
configure:9491: checking for ld used by g++
configure:9558: result: /usr/bin/ld
configure:9567: checking if the linker (/usr/bin/ld) is GNU ld
configure:9582: result: yes
configure:9633: checking whether the g++ linker (/usr/bin/ld) supports shared libraries
configure:10441: result: yes
configure:10459: g++ -c -g -O2  conftest.cc >&5
configure:10462: $? = 0
configure:10558: checking for g++ option to produce PIC
configure:10810: result: -fPIC
configure:10818: checking if g++ PIC flag -fPIC works
configure:10836: g++ -c -g -O2  -fPIC -DPIC conftest.cc >&5
configure:10840: $? = 0
configure:10851: result: yes
configure:10875: checking if g++ supports -c -o file.o
configure:10896: g++ -c -g -O2  -o out/conftest2.o conftest.cc >&5
configure:10900: $? = 0
configure:10920: result: yes
configure:10946: checking whether the g++ linker (/usr/bin/ld) supports shared libraries
configure:10971: result: yes
configure:11042: checking dynamic linker characteristics
configure:11582: result: GNU/Linux ld.so
configure:11586: checking how to hardcode library paths into programs
configure:11611: result: immediate
configure:11625: checking whether stripping libraries is possible
configure:11630: result: yes
configure:18651: checking whether ln -s works
configure:18655: result: yes
configure:18670: checking for g++
configure:18686: found /usr/bin/g++
configure:18697: result: yes
configure:18741: checking for qt_null in -lqthreads
configure:18772: gcc -o conftest -g -O2    conftest.c -lqthreads   >&5
/usr/bin/ld: cannot find -lqthreads
collect2: ld returned 1 exit status
configure:18775: $? = 1
configure: failed program was:
| #line 18748 "configure"
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "gnome-games"
| #define PACKAGE_TARNAME "gnome-games"
| #define PACKAGE_VERSION "2.6.2"
| #define PACKAGE_STRING "gnome-games 2.6.2"
| #define PACKAGE_BUGREPORT "http://bugzilla.gnome.org/enter_bug.cgi?product=gnome-games"
| #define PACKAGE "gnome-games"
| #define VERSION "2.6.2"
| #ifdef __cplusplus
| #include <stdlib.h>
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| /* end confdefs.h.  */
| 
| /* Override any gcc2 internal prototype to avoid an error.  */
| #ifdef __cplusplus
| extern "C"
| #endif
| /* We use char because int might match the return type of a gcc2
|    builtin and then its argument prototype would still apply.  */
| char qt_null ();
| int
| main ()
| {
| qt_null ();
|   ;
|   return 0;
| }
configure:18793: result: no
configure:18801: checking for qt_null in -lqt
configure:18832: gcc -o conftest -g -O2    conftest.c -lqt   >&5
/usr/bin/ld: cannot find -lqt
collect2: ld returned 1 exit status
configure:18835: $? = 1
configure: failed program was:
| #line 18808 "configure"
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "gnome-games"
| #define PACKAGE_TARNAME "gnome-games"
| #define PACKAGE_VERSION "2.6.2"
| #define PACKAGE_STRING "gnome-games 2.6.2"
| #define PACKAGE_BUGREPORT "http://bugzilla.gnome.org/enter_bug.cgi?product=gnome-games"
| #define PACKAGE "gnome-games"
| #define VERSION "2.6.2"
| #ifdef __cplusplus
| #include <stdlib.h>
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| /* end confdefs.h.  */
| 
| /* Override any gcc2 internal prototype to avoid an error.  */
| #ifdef __cplusplus
| extern "C"
| #endif
| /* We use char because int might match the return type of a gcc2
|    builtin and then its argument prototype would still apply.  */
| char qt_null ();
| int
| main ()
| {
| qt_null ();
|   ;
|   return 0;
| }
configure:18853: result: no
configure:18864: checking for main in -ltermcap
configure:18889: gcc -o conftest -g -O2    conftest.c -ltermcap   >&5
configure:18892: $? = 0
configure:18895: test -s conftest
configure:18898: $? = 0
configure:18910: result: yes
configure:18916: checking for main in -lreadline
configure:18941: gcc -o conftest -g -O2    conftest.c -lreadline -ltermcap  >&5
configure:18944: $? = 0
configure:18947: test -s conftest
configure:18950: $? = 0
configure:18962: result: yes
configure:18980: checking for guile-config
configure:18996: found /usr/bin/guile-config
configure:19007: result: yes
configure:19016: checking whether guile-config works
configure:19022: result: yes
configure:19082: checking for sin in -lm
configure:19113: gcc -o conftest -g -O2    conftest.c -lm   >&5
configure:19120: warning: conflicting types for built-in function 'sin'
configure:19116: $? = 0
configure:19119: test -s conftest
configure:19122: $? = 0
configure:19134: result: yes
configure:19147: checking for guile libraries
configure:19150: result:  -pthread -lguile -lltdl  -Wl,-Bsymbolic-functions -lgmp -lcrypt -lm -lltdl
configure:19152: checking for guile headers
configure:19155: result:   -pthread
configure:19454: checking whether guile works
configure:19479: gcc -o conftest -g -O2    -pthread   conftest.c -lm   -pthread -lguile -lltdl  -Wl,-Bsymbolic-functions -lgmp -lcrypt -lm -lltdl >&5
In file included from /usr/local/include/libguile.h:91,
                 from configure:19482:
/usr/local/include/libguile/numbers.h:35:21: error: ieeefp.h: No such file or directory
configure:19482: $? = 1
configure: failed program was:
| #line 19456 "configure"
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "gnome-games"
| #define PACKAGE_TARNAME "gnome-games"
| #define PACKAGE_VERSION "2.6.2"
| #define PACKAGE_STRING "gnome-games 2.6.2"
| #define PACKAGE_BUGREPORT "http://bugzilla.gnome.org/enter_bug.cgi?product=gnome-games"
| #define PACKAGE "gnome-games"
| #define VERSION "2.6.2"
| #ifdef __cplusplus
| #include <stdlib.h>
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| #define HAVE_LIBM 1
| /* end confdefs.h.  */
| 
| 		#include <libguile.h>
| 		#include <guile/gh.h>
| 
| int
| main ()
| {
| 
| 		gh_eval_str("(newline)");
| 		scm_boot_guile(0,NULL,NULL,NULL);
| 
|   ;
|   return 0;
| }
configure:19507: result: no
configure:19518: WARNING: Can not find Guile on this system
configure:19643: checking what warning flags to pass to the C compiler
configure:19645: result: -Wall -Wmissing-prototypes
configure:19656: checking what language compliance flags to pass to the C compiler
configure:19671: result: 
configure:19686: checking what warning flags to pass to the C++ compiler
configure:19706: result: -Wall -Wno-unused
configure:19717: checking what language compliance flags to pass to the C++ compiler
configure:19733: result: 
configure:19756: result: Using config source xml:merged:/etc/gconf/gconf.xml.defaults for schema installation
configure:19773: result: Using $(sysconfdir)/gconf/schemas/ as install directory for schema files
configure:19802: checking for gconftool-2
configure:19820: found /usr/bin/gconftool-2
configure:19832: result: /usr/bin/gconftool-2
configure:19849: checking for scrollkeeper-config
configure:19867: found /usr/bin/scrollkeeper-config
configure:19880: result: /usr/bin/scrollkeeper-config
configure:19907: checking for pkg-config
configure:19925: found /usr/bin/pkg-config
configure:19938: result: /usr/bin/pkg-config
configure:19955: checking for libglade-2.0 libgnome-2.0 >= 1.105.0 libgnomeui-2.0 >= 1.105.0 gconf-2.0 >= 2.3 gnome-vfs-module-2.0 >= 1.9.11 gtk+-2.0 >= 2.3 librsvg-2.0 >= 2.0
configure:19959: result: yes
configure:19963: checking GNOME_GAMES_CFLAGS
configure:19966: result: -pthread -DORBIT2=1 -I/usr/local/include/gio-standalone -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libgnome-2.0 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/bonobo-activation-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gail-1.0 -I/usr/include/gnome-vfs-module-2.0 -I/usr/include/librsvg-2  
configure:19969: checking GNOME_GAMES_LIBS
configure:19972: result: -pthread -L/usr/local/lib -lglade-2.0 -lxml2 -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lORBit-2 -lart_lgpl_2 -lgnomevfs-2 -lgconf-2 -lgthread-2.0 -lrt -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgio -lpango-1.0 -lfreetype -lz -lfontconfig -lrsvg-2 -lgdk_pixbuf-2.0 -lm -lcairo -lgobject-2.0 -lgmodule-2.0 -lglib-2.0  
configure:20069: checking for esound
configure:20073: result: yes
configure:20077: checking ESD_CFLAGS
configure:20080: result:  
configure:20083: checking ESD_LIBS
configure:20086: result: -lesd -laudiofile  
configure:20142: checking locale.h usability
configure:20155: gcc -c -g -O2  conftest.c >&5
configure:20158: $? = 0
configure:20161: test -s conftest.o
configure:20164: $? = 0
configure:20174: result: yes
configure:20178: checking locale.h presence
configure:20189: gcc -E  conftest.c
configure:20195: $? = 0
configure:20214: result: yes
configure:20250: checking for locale.h
configure:20257: result: yes
configure:20271: checking for LC_MESSAGES
configure:20293: gcc -o conftest -g -O2   conftest.c -lm  >&5
configure:20296: $? = 0
configure:20299: test -s conftest
configure:20302: $? = 0
configure:20313: result: yes
configure:20342: checking libintl.h usability
configure:20355: gcc -c -g -O2  conftest.c >&5
configure:20358: $? = 0
configure:20361: test -s conftest.o
configure:20364: $? = 0
configure:20374: result: yes
configure:20378: checking libintl.h presence
configure:20389: gcc -E  conftest.c
configure:20395: $? = 0
configure:20414: result: yes
configure:20450: checking for libintl.h
configure:20457: result: yes
configure:20468: checking for dgettext in libc
configure:20492: gcc -o conftest -g -O2   conftest.c -lm  >&5
configure:20495: $? = 0
configure:20498: test -s conftest
configure:20501: $? = 0
configure:20513: result: yes
configure:20521: checking for bind_textdomain_codeset
configure:20571: gcc -o conftest -g -O2   conftest.c -lm  >&5
configure:20574: $? = 0
configure:20577: test -s conftest
configure:20580: $? = 0
configure:20591: result: yes
configure:20915: checking for msgfmt
configure:20942: result: /usr/bin/msgfmt
configure:20955: checking for dcgettext
configure:21005: gcc -o conftest -g -O2   conftest.c -lm   >&5
configure:21006: warning: conflicting types for built-in function 'dcgettext'
configure:21008: $? = 0
configure:21011: test -s conftest
configure:21014: $? = 0
configure:21025: result: yes
configure:21037: checking for gmsgfmt
configure:21068: result: /usr/bin/msgfmt
configure:21077: checking for xgettext
configure:21104: result: /usr/bin/xgettext
configure:21129: gcc -o conftest -g -O2   conftest.c -lm   >&5
configure:21132: $? = 0
configure:21135: test -s conftest
configure:21138: $? = 0
configure:21292: checking for catalogs to be installed
configure:21317: result:  am ar az be bg bn ca cs cy da de el en_CA en_GB es et eu fa fi fr ga gl gu he hi hr hu id it ja ko lt lv mk ml mn ms nl nn no pa pl pt pt_BR ro ru sk sl sq sr sr@Latn sv tr uk vi wa zh_CN zh_TW
configure:21354: checking for ngettext
configure:21404: gcc -o conftest -g -O2   conftest.c -lm  >&5
configure:21407: $? = 0
configure:21410: test -s conftest
configure:21413: $? = 0
configure:21424: result: yes
configure:21436: checking for ANSI C header files
configure:21586: result: yes
configure:21599: checking for stdbool.h that conforms to C99
configure:21653: gcc -c -g -O2  conftest.c >&5
configure:21656: $? = 0
configure:21659: test -s conftest.o
configure:21662: $? = 0
configure:21673: result: yes
configure:21675: checking for _Bool
configure:21700: gcc -c -g -O2  conftest.c >&5
configure:21703: $? = 0
configure:21706: test -s conftest.o
configure:21709: $? = 0
configure:21720: result: yes
configure:21739: checking for an ANSI C-conforming const
configure:21807: gcc -c -g -O2  conftest.c >&5
configure:21810: $? = 0
configure:21813: test -s conftest.o
configure:21816: $? = 0
configure:21827: result: yes
configure:21837: checking for inline
configure:21859: gcc -c -g -O2  conftest.c >&5
configure:21862: $? = 0
configure:21865: test -s conftest.o
configure:21868: $? = 0
configure:21880: result: inline
configure:21911: checking sys/dir.h usability
configure:21924: gcc -c -g -O2  conftest.c >&5
configure:21927: $? = 0
configure:21930: test -s conftest.o
configure:21933: $? = 0
configure:21943: result: yes
configure:21947: checking sys/dir.h presence
configure:21958: gcc -E  conftest.c
configure:21964: $? = 0
configure:21983: result: yes
configure:22019: checking for sys/dir.h
configure:22026: result: yes
configure:22097: checking sys/dirent.h usability
configure:22110: gcc -c -g -O2  conftest.c >&5
configure:22169:24: error: sys/dirent.h: No such file or directory
configure:22113: $? = 1
configure: failed program was:
| #line 22099 "configure"
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "gnome-games"
| #define PACKAGE_TARNAME "gnome-games"
| #define PACKAGE_VERSION "2.6.2"
| #define PACKAGE_STRING "gnome-games 2.6.2"
| #define PACKAGE_BUGREPORT "http://bugzilla.gnome.org/enter_bug.cgi?product=gnome-games"
| #define PACKAGE "gnome-games"
| #define VERSION "2.6.2"
| #ifdef __cplusplus
| #include <stdlib.h>
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| #define HAVE_LIBM 1
| #define GETTEXT_PACKAGE "gnome-games"
| #define HAVE_LOCALE_H 1
| #define HAVE_LC_MESSAGES 1
| #define HAVE_BIND_TEXTDOMAIN_CODESET 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define ENABLE_NLS 1
| #define HAVE_NGETTEXT 1
| #define STDC_HEADERS 1
| #define HAVE__BOOL 1
| #define HAVE_STDBOOL_H 1
| /* end confdefs.h.  */
| #include <stdio.h>
| #if HAVE_SYS_TYPES_H
| # include <sys/types.h>
| #endif
| #if HAVE_SYS_STAT_H
| # include <sys/stat.h>
| #endif
| #if STDC_HEADERS
| # include <stdlib.h>
| # include <stddef.h>
| #else
| # if HAVE_STDLIB_H
| #  include <stdlib.h>
| # endif
| #endif
| #if HAVE_STRING_H
| # if !STDC_HEADERS && HAVE_MEMORY_H
| #  include <memory.h>
| # endif
| # include <string.h>
| #endif
| #if HAVE_STRINGS_H
| # include <strings.h>
| #endif
| #if HAVE_INTTYPES_H
| # include <inttypes.h>
| #else
| # if HAVE_STDINT_H
| #  include <stdint.h>
| # endif
| #endif
| #if HAVE_UNISTD_H
| # include <unistd.h>
| #endif
| #include <sys/dirent.h>
configure:22129: result: no
configure:22133: checking sys/dirent.h presence
configure:22144: gcc -E  conftest.c
configure:22171:24: error: sys/dirent.h: No such file or directory
configure:22150: $? = 1
configure: failed program was:
| #line 22135 "configure"
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "gnome-games"
| #define PACKAGE_TARNAME "gnome-games"
| #define PACKAGE_VERSION "2.6.2"
| #define PACKAGE_STRING "gnome-games 2.6.2"
| #define PACKAGE_BUGREPORT "http://bugzilla.gnome.org/enter_bug.cgi?product=gnome-games"
| #define PACKAGE "gnome-games"
| #define VERSION "2.6.2"
| #ifdef __cplusplus
| #include <stdlib.h>
| #endif
| #define STDC_HEADERS 1
| #define HAVE_SYS_TYPES_H 1
| #define HAVE_SYS_STAT_H 1
| #define HAVE_STDLIB_H 1
| #define HAVE_STRING_H 1
| #define HAVE_MEMORY_H 1
| #define HAVE_STRINGS_H 1
| #define HAVE_INTTYPES_H 1
| #define HAVE_STDINT_H 1
| #define HAVE_UNISTD_H 1
| #define HAVE_DLFCN_H 1
| #define HAVE_LIBM 1
| #define GETTEXT_PACKAGE "gnome-games"
| #define HAVE_LOCALE_H 1
| #define HAVE_LC_MESSAGES 1
| #define HAVE_BIND_TEXTDOMAIN_CODESET 1
| #define HAVE_GETTEXT 1
| #define HAVE_DCGETTEXT 1
| #define ENABLE_NLS 1
| #define HAVE_NGETTEXT 1
| #define STDC_HEADERS 1
| #define HAVE__BOOL 1
| #define HAVE_STDBOOL_H 1
| /* end confdefs.h.  */
| #include <sys/dirent.h>
configure:22169: result: no
configure:22205: checking for sys/dirent.h
configure:22212: result: no
configure:22232: checking if sys/dir.h defines struct direct or dirent
configure:22251: gcc -c -g -O2  conftest.c >&5
configure:22254: $? = 0
configure:22257: test -s conftest.o
configure:22260: $? = 0
configure:22262: result: direct
configure:22320: checking for scandir
configure:22370: gcc -o conftest -g -O2   conftest.c -lm  >&5
configure:22373: $? = 0
configure:22376: test -s conftest
configure:22379: $? = 0
configure:22390: result: yes
configure:22740: creating ./config.status

## ---------------------- ##
## Running config.status. ##
## ---------------------- ##

This file was extended by gnome-games config.status 2.6.2, which was
generated by GNU Autoconf 2.57.  Invocation command line was

  CONFIG_FILES    = 
  CONFIG_HEADERS  = 
  CONFIG_LINKS    = 
  CONFIG_COMMANDS = 
  $ ./config.status 

on irwin-laptop

config.status:823: creating gnome-games.spec
config.status:823: creating Makefile
config.status:823: creating po/Makefile.in
config.status:823: creating libgames-support/Makefile
config.status:823: creating blackjack/Makefile
config.status:823: creating blackjack/data/Makefile
config.status:823: creating blackjack/help/Makefile
config.status:823: creating blackjack/help/C/Makefile
config.status:823: creating blackjack/pixmaps/Makefile
config.status:823: creating blackjack/src/Makefile
config.status:823: creating gnect/Makefile
config.status:823: creating gnect/src/Makefile
config.status:823: creating gnect/data/Makefile
config.status:823: creating gnect/pixmaps/Makefile
config.status:823: creating gnect/help/Makefile
config.status:823: creating gnect/help/C/Makefile
config.status:823: creating gnomine/Makefile
config.status:823: creating gnomine/help/Makefile
config.status:823: creating gnomine/help/C/Makefile
config.status:823: creating gnome-stones/Makefile
config.status:823: creating gnome-stones/graphics/Makefile
config.status:823: creating gnome-stones/objects/Makefile
config.status:823: creating gnome-stones/sounds/Makefile
config.status:823: creating gnome-stones/help/Makefile
config.status:823: creating gnome-stones/help/C/Makefile
config.status:823: creating same-gnome/Makefile
config.status:823: creating same-gnome/help/Makefile
config.status:823: creating same-gnome/help/C/Makefile
config.status:823: creating mahjongg/Makefile
config.status:823: creating mahjongg/help/Makefile
config.status:823: creating mahjongg/help/C/Makefile
config.status:823: creating gtali/Makefile
config.status:823: creating gtali/pix/Makefile
config.status:823: creating gtali/help/Makefile
config.status:823: creating gtali/help/C/Makefile
config.status:823: creating gtali/help/da/Makefile
config.status:823: creating iagno/Makefile
config.status:823: creating iagno/sounds/Makefile
config.status:823: creating iagno/help/Makefile
config.status:823: creating iagno/help/C/Makefile
config.status:823: creating gataxx/Makefile
config.status:823: creating gataxx/sounds/Makefile
config.status:823: creating gataxx/help/Makefile
config.status:823: creating gataxx/help/C/Makefile
config.status:823: creating gnotravex/Makefile
config.status:823: creating gnotravex/help/Makefile
config.status:823: creating gnotravex/help/C/Makefile
config.status:823: creating gnotski/Makefile
config.status:823: creating gnotski/help/Makefile
config.status:823: creating gnotski/help/C/Makefile
config.status:823: creating glines/Makefile
config.status:823: creating glines/help/Makefile
config.status:823: creating glines/help/C/Makefile
config.status:823: creating gdk-card-image/Makefile
config.status:823: creating gnometris/Makefile
config.status:823: creating gnometris/pix/Makefile
config.status:823: creating gnometris/help/Makefile
config.status:823: creating gnometris/help/C/Makefile
config.status:823: creating gnobots2/Makefile
config.status:823: creating gnobots2/help/Makefile
config.status:823: creating gnobots2/help/C/Makefile
config.status:823: creating gnobots2/help/da/Makefile
config.status:823: creating gnobots2/help/es/Makefile
config.status:823: creating gnobots2/help/it/Makefile
config.status:823: creating gnibbles/Makefile
config.status:823: creating gnibbles/help/Makefile
config.status:823: creating gnibbles/help/C/Makefile
config.status:823: creating gnibbles/sounds/Makefile
config.status:823: creating aisleriot/Makefile
config.status:823: creating aisleriot/help/Makefile
config.status:823: creating aisleriot/help/C/Makefile
config.status:927: creating config.h
config.status:1186: executing depfiles commands
config.status:1186: executing default-1 commands
config.status:1186: executing default-2 commands

## ---------------- ##
## Cache variables. ##
## ---------------- ##

ac_cv_build=i686-pc-linux-gnu
ac_cv_build_alias=i686-pc-linux-gnu
ac_cv_c_compiler_gnu=yes
ac_cv_c_const=yes
ac_cv_c_inline=inline
ac_cv_cxx_compiler_gnu=yes
ac_cv_env_CC_set=
ac_cv_env_CC_value=
ac_cv_env_CFLAGS_set=
ac_cv_env_CFLAGS_value=
ac_cv_env_CPPFLAGS_set=
ac_cv_env_CPPFLAGS_value=
ac_cv_env_CPP_set=
ac_cv_env_CPP_value=
ac_cv_env_CXXCPP_set=
ac_cv_env_CXXCPP_value=
ac_cv_env_CXXFLAGS_set=
ac_cv_env_CXXFLAGS_value=
ac_cv_env_CXX_set=
ac_cv_env_CXX_value=
ac_cv_env_F77_set=
ac_cv_env_F77_value=
ac_cv_env_FFLAGS_set=
ac_cv_env_FFLAGS_value=
ac_cv_env_LDFLAGS_set=
ac_cv_env_LDFLAGS_value=
ac_cv_env_build_alias_set=
ac_cv_env_build_alias_value=
ac_cv_env_host_alias_set=
ac_cv_env_host_alias_value=
ac_cv_env_target_alias_set=
ac_cv_env_target_alias_value=
ac_cv_exeext=
ac_cv_f77_compiler_gnu=no
ac_cv_func_bind_textdomain_codeset=yes
ac_cv_func_dcgettext=yes
ac_cv_func_ngettext=yes
ac_cv_func_scandir=yes
ac_cv_guile_found=no
ac_cv_header_dlfcn_h=yes
ac_cv_header_inttypes_h=yes
ac_cv_header_libintl_h=yes
ac_cv_header_locale_h=yes
ac_cv_header_memory_h=yes
ac_cv_header_stdbool_h=yes
ac_cv_header_stdc=yes
ac_cv_header_stdint_h=yes
ac_cv_header_stdlib_h=yes
ac_cv_header_string_h=yes
ac_cv_header_strings_h=yes
ac_cv_header_sys_dir_h=yes
ac_cv_header_sys_dirent_h=no
ac_cv_header_sys_stat_h=yes
ac_cv_header_sys_types_h=yes
ac_cv_header_unistd_h=yes
ac_cv_host=i686-pc-linux-gnu
ac_cv_host_alias=i686-pc-linux-gnu
ac_cv_lib_m_sin=yes
ac_cv_lib_qt_qt_null=no
ac_cv_lib_qthreads_qt_null=no
ac_cv_lib_readline_main=yes
ac_cv_lib_termcap_main=yes
ac_cv_objext=o
ac_cv_path_GCONFTOOL=/usr/bin/gconftool-2
ac_cv_path_GMSGFMT=/usr/bin/msgfmt
ac_cv_path_INTLTOOL_PERL=/usr/bin/perl
ac_cv_path_MSGFMT=/usr/bin/msgfmt
ac_cv_path_PKG_CONFIG=/usr/bin/pkg-config
ac_cv_path_SCROLLKEEPER_CONFIG=/usr/bin/scrollkeeper-config
ac_cv_path_XGETTEXT=/usr/bin/xgettext
ac_cv_path_install='/usr/bin/install -c'
ac_cv_prog_AWK=gawk
ac_cv_prog_BUILD_GUILE=yes
ac_cv_prog_CPP='gcc -E'
ac_cv_prog_CXXCPP='g++ -E'
ac_cv_prog_CXX_PRESENT=yes
ac_cv_prog_ac_ct_AR=ar
ac_cv_prog_ac_ct_CC=gcc
ac_cv_prog_ac_ct_CXX=g++
ac_cv_prog_ac_ct_RANLIB=ranlib
ac_cv_prog_ac_ct_STRIP=strip
ac_cv_prog_cc_g=yes
ac_cv_prog_cc_stdc=
ac_cv_prog_cxx_g=yes
ac_cv_prog_egrep='grep -E'
ac_cv_prog_f77_g=no
ac_cv_prog_make_make_set=yes
ac_cv_type__Bool=yes
am_cv_CC_dependencies_compiler_type=gcc3
am_cv_CXX_dependencies_compiler_type=gcc3
am_cv_val_LC_MESSAGES=yes
gt_cv_func_dgettext_libc=yes
gt_cv_func_dgettext_libintl=no
gt_cv_have_gettext=yes
lt_cv_deplibs_check_method=pass_all
lt_cv_file_magic_cmd='$MAGIC_CMD'
lt_cv_file_magic_test_file='/lib/libc.so.6 /lib/libc-2.8.90.so'
lt_cv_ld_reload_flag=-r
lt_cv_objdir=.libs
lt_cv_path_LD=/usr/bin/ld
lt_cv_path_LDCXX=/usr/bin/ld
lt_cv_path_NM='/usr/bin/nm -B'
lt_cv_path_SED=/bin/sed
lt_cv_prog_compiler_c_o=yes
lt_cv_prog_compiler_c_o_CXX=yes
lt_cv_prog_compiler_rtti_exceptions=no
lt_cv_prog_gnu_ld=yes
lt_cv_prog_gnu_ldcxx=yes
lt_cv_sys_global_symbol_pipe='sed -n -e '\''s/^.*[ 	]\([ABCDGIRSTW][ABCDGIRSTW]*\)[ 	][ 	]*\(\)\([_A-Za-z][_A-Za-z0-9]*\)$/\1 \2\3 \3/p'\'''
lt_cv_sys_global_symbol_to_c_name_address='sed -n -e '\''s/^: \([^ ]*\) $/  {\"\1\", (lt_ptr) 0},/p'\'' -e '\''s/^[BCDEGRST] \([^ ]*\) \([^ ]*\)$/  {"\2", (lt_ptr) \&\2},/p'\'''
lt_cv_sys_global_symbol_to_cdecl='sed -n -e '\''s/^. .* \(.*\)$/extern int \1;/p'\'''
lt_cv_sys_max_cmd_len=32768
lt_lt_cv_prog_compiler_c_o='"yes"'
lt_lt_cv_prog_compiler_c_o_CXX='"yes"'
lt_lt_cv_sys_global_symbol_pipe='"sed -n -e '\''s/^.*[ 	]\\([ABCDGIRSTW][ABCDGIRSTW]*\\)[ 	][ 	]*\\(\\)\\([_A-Za-z][_A-Za-z0-9]*\\)\$/\\1 \\2\\3 \\3/p'\''"'
lt_lt_cv_sys_global_symbol_to_c_name_address='"sed -n -e '\''s/^: \\([^ ]*\\) \$/  {\\\"\\1\\\", (lt_ptr) 0},/p'\'' -e '\''s/^[BCDEGRST] \\([^ ]*\\) \\([^ ]*\\)\$/  {\"\\2\", (lt_ptr) \\&\\2},/p'\''"'
lt_lt_cv_sys_global_symbol_to_cdecl='"sed -n -e '\''s/^. .* \\(.*\\)\$/extern int \\1;/p'\''"'

## ----------------- ##
## Output variables. ##
## ----------------- ##

ACLOCAL='${SHELL} /home/jordan/Desktop/gnome-games-2.6.2/missing --run aclocal-1.7'
ACLOCAL_AMFLAGS=''
AMDEPBACKSLASH='\'
AMDEP_FALSE='#'
AMDEP_TRUE=''
AMTAR='${SHELL} /home/jordan/Desktop/gnome-games-2.6.2/missing --run tar'
AR='ar'
AUTOCONF='${SHELL} /home/jordan/Desktop/gnome-games-2.6.2/missing --run autoconf'
AUTOHEADER='${SHELL} /home/jordan/Desktop/gnome-games-2.6.2/missing --run autoheader'
AUTOMAKE='${SHELL} /home/jordan/Desktop/gnome-games-2.6.2/missing --run automake-1.7'
AWK='gawk'
BUILD_GUILE='yes'
CATALOGS=' am.gmo ar.gmo az.gmo be.gmo bg.gmo bn.gmo ca.gmo cs.gmo cy.gmo da.gmo de.gmo el.gmo en_CA.gmo en_GB.gmo es.gmo et.gmo eu.gmo fa.gmo fi.gmo fr.gmo ga.gmo gl.gmo gu.gmo he.gmo hi.gmo hr.gmo hu.gmo id.gmo it.gmo ja.gmo ko.gmo lt.gmo lv.gmo mk.gmo ml.gmo mn.gmo ms.gmo nl.gmo nn.gmo no.gmo pa.gmo pl.gmo pt.gmo pt_BR.gmo ro.gmo ru.gmo sk.gmo sl.gmo sq.gmo sr.gmo sr@Latn.gmo sv.gmo tr.gmo uk.gmo vi.gmo wa.gmo zh_CN.gmo zh_TW.gmo'
CATOBJEXT='.gmo'
CC='gcc'
CCDEPMODE='depmode=gcc3'
CFLAGS='-g -O2'
CPP='gcc -E'
CPPFLAGS=''
CXX='g++'
CXXCPP='g++ -E'
CXXDEPMODE='depmode=gcc3'
CXXFLAGS='-g -O2'
CXX_PRESENT='yes'
CYGPATH_W='echo'
DATADIRNAME='share'
DEFS='-DHAVE_CONFIG_H'
DEPDIR='.deps'
ECHO='echo'
ECHO_C=''
ECHO_N='-n'
ECHO_T=''
EGREP='grep -E'
ESD_CFLAGS=' '
ESD_LIBS='-lesd -laudiofile  '
EXEEXT=''
F77=''
FFLAGS=''
GCONFTOOL='/usr/bin/gconftool-2'
GCONF_SCHEMAS_INSTALL_FALSE='#'
GCONF_SCHEMAS_INSTALL_TRUE=''
GCONF_SCHEMA_CONFIG_SOURCE='xml:merged:/etc/gconf/gconf.xml.defaults'
GCONF_SCHEMA_FILE_DIR='$(sysconfdir)/gconf/schemas/'
GETTEXT_PACKAGE='gnome-games'
GMOFILES=' am.gmo ar.gmo az.gmo be.gmo bg.gmo bn.gmo ca.gmo cs.gmo cy.gmo da.gmo de.gmo el.gmo en_CA.gmo en_GB.gmo es.gmo et.gmo eu.gmo fa.gmo fi.gmo fr.gmo ga.gmo gl.gmo gu.gmo he.gmo hi.gmo hr.gmo hu.gmo id.gmo it.gmo ja.gmo ko.gmo lt.gmo lv.gmo mk.gmo ml.gmo mn.gmo ms.gmo nl.gmo nn.gmo no.gmo pa.gmo pl.gmo pt.gmo pt_BR.gmo ro.gmo ru.gmo sk.gmo sl.gmo sq.gmo sr.gmo sr@Latn.gmo sv.gmo tr.gmo uk.gmo vi.gmo wa.gmo zh_CN.gmo zh_TW.gmo'
GMSGFMT='/usr/bin/msgfmt'
GNOME_GAMES_CFLAGS='-std=gnu89 -pthread -DORBIT2=1 -I/usr/local/include/gio-standalone -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libgnome-2.0 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/bonobo-activation-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gail-1.0 -I/usr/include/gnome-vfs-module-2.0 -I/usr/include/librsvg-2   -I$(top_srcdir)/libgames-support -Wall -Wmissing-prototypes '
GNOME_GAMES_CXXFLAGS='-pthread -DORBIT2=1 -I/usr/local/include/gio-standalone -I/usr/local/include/glib-2.0 -I/usr/local/lib/glib-2.0/include -I/usr/include/libglade-2.0 -I/usr/include/gtk-2.0 -I/usr/include/libxml2 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pango-1.0 -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libgnome-2.0 -I/usr/include/orbit-2.0 -I/usr/include/gconf/2 -I/usr/include/gnome-vfs-2.0 -I/usr/lib/gnome-vfs-2.0/include -I/usr/include/libbonobo-2.0 -I/usr/include/dbus-1.0 -I/usr/lib/dbus-1.0/include -I/usr/include/bonobo-activation-2.0 -I/usr/include/libgnomeui-2.0 -I/usr/include/libart-2.0 -I/usr/include/gnome-keyring-1 -I/usr/include/libbonoboui-2.0 -I/usr/include/libgnomecanvas-2.0 -I/usr/include/gail-1.0 -I/usr/include/gnome-vfs-module-2.0 -I/usr/include/librsvg-2   -I$(top_srcdir)/libgames-support -Wall -Wmissing-prototypes '
GNOME_GAMES_LIBS='-pthread -L/usr/local/lib -lglade-2.0 -lxml2 -lgnomeui-2 -lSM -lICE -lbonoboui-2 -lgnomecanvas-2 -lgnome-2 -lpopt -lbonobo-2 -lbonobo-activation -lORBit-2 -lart_lgpl_2 -lgnomevfs-2 -lgconf-2 -lgthread-2.0 -lrt -lgtk-x11-2.0 -lgdk-x11-2.0 -latk-1.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgio -lpango-1.0 -lfreetype -lz -lfontconfig -lrsvg-2 -lgdk_pixbuf-2.0 -lm -lcairo -lgobject-2.0 -lgmodule-2.0 -lglib-2.0   $(top_builddir)/libgames-support/libgames-support.la'
GUILE_FALSE=''
GUILE_INCS=''
GUILE_LIBS=''
GUILE_TRUE='#'
HAVE_CXX_FALSE='#'
HAVE_CXX_TRUE=''
INSTALL_DATA='${INSTALL} -m 644'
INSTALL_PROGRAM='${INSTALL}'
INSTALL_SCRIPT='${INSTALL}'
INSTALL_STRIP_PROGRAM='${SHELL} $(install_sh) -c -s'
INSTOBJEXT='.mo'
INTLLIBS=''
INTLTOOL_CAVES_RULE='%.caves:     %.caves.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -d -u -c $(top_builddir)/po/.intltool-merge-cache'
INTLTOOL_DESKTOP_RULE='%.desktop:   %.desktop.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -d -u -c $(top_builddir)/po/.intltool-merge-cache'
INTLTOOL_DIRECTORY_RULE='%.directory: %.directory.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -d -u -c $(top_builddir)/po/.intltool-merge-cache'
INTLTOOL_EXTRACT='$(top_builddir)/intltool-extract'
INTLTOOL_KBD_RULE='%.kbd:       %.kbd.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -x -u -m -c $(top_builddir)/po/.intltool-merge-cache'
INTLTOOL_KEYS_RULE='%.keys:      %.keys.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -k -u -c $(top_builddir)/po/.intltool-merge-cache'
INTLTOOL_MERGE='$(top_builddir)/intltool-merge'
INTLTOOL_OAF_RULE='%.oaf:       %.oaf.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -o -p'
INTLTOOL_PERL='/usr/bin/perl'
INTLTOOL_PONG_RULE='%.pong:      %.pong.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -x -u -c $(top_builddir)/po/.intltool-merge-cache'
INTLTOOL_PROP_RULE='%.prop:      %.prop.in      $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -d -u -c $(top_builddir)/po/.intltool-merge-cache'
INTLTOOL_SCHEMAS_RULE='%.schemas:   %.schemas.in   $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -s -u -c $(top_builddir)/po/.intltool-merge-cache'
INTLTOOL_SERVER_RULE='%.server:    %.server.in    $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -o -u -c $(top_builddir)/po/.intltool-merge-cache'
INTLTOOL_SHEET_RULE='%.sheet:     %.sheet.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -x -u -c $(top_builddir)/po/.intltool-merge-cache'
INTLTOOL_SOUNDLIST_RULE='%.soundlist: %.soundlist.in $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -d -u -c $(top_builddir)/po/.intltool-merge-cache'
INTLTOOL_THEME_RULE='%.theme:     %.theme.in     $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -d -u -c $(top_builddir)/po/.intltool-merge-cache'
INTLTOOL_UI_RULE='%.ui:        %.ui.in        $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -x -u -c $(top_builddir)/po/.intltool-merge-cache'
INTLTOOL_UPDATE='$(top_builddir)/intltool-update'
INTLTOOL_XAM_RULE='%.xam:       %.xml.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -x -u -c $(top_builddir)/po/.intltool-merge-cache'
INTLTOOL_XML_RULE='%.xml:       %.xml.in       $(INTLTOOL_MERGE) $(wildcard $(top_srcdir)/po/*.po) ; LC_ALL=C $(INTLTOOL_MERGE) $(top_srcdir)/po $< $@ -x -u -c $(top_builddir)/po/.intltool-merge-cache'
LDFLAGS=''
LIBOBJS=''
LIBS='-lm '
LIBTOOL='$(SHELL) $(top_builddir)/libtool'
LN_S='ln -s'
LTLIBOBJS=''
MAINT='#'
MAINTAINER_MODE_FALSE=''
MAINTAINER_MODE_TRUE='#'
MAKEINFO='${SHELL} /home/jordan/Desktop/gnome-games-2.6.2/missing --run makeinfo'
MKINSTALLDIRS='./mkinstalldirs'
MSGFMT='/usr/bin/msgfmt'
OBJEXT='o'
PACKAGE='gnome-games'
PACKAGE_BUGREPORT='http://bugzilla.gnome.org/enter_bug.cgi?product=gnome-games'
PACKAGE_NAME='gnome-games'
PACKAGE_STRING='gnome-games 2.6.2'
PACKAGE_TARNAME='gnome-games'
PACKAGE_VERSION='2.6.2'
PATH_SEPARATOR=':'
PKG_CONFIG='/usr/bin/pkg-config'
POFILES=' am.po ar.po az.po be.po bg.po bn.po ca.po cs.po cy.po da.po de.po el.po en_CA.po en_GB.po es.po et.po eu.po fa.po fi.po fr.po ga.po gl.po gu.po he.po hi.po hr.po hu.po id.po it.po ja.po ko.po lt.po lv.po mk.po ml.po mn.po ms.po nl.po nn.po no.po pa.po pl.po pt.po pt_BR.po ro.po ru.po sk.po sl.po sq.po sr.po sr@Latn.po sv.po tr.po uk.po vi.po wa.po zh_CN.po zh_TW.po'
POSUB='po'
PO_IN_DATADIR_FALSE=''
PO_IN_DATADIR_TRUE=''
QTTHREADS_LIB=''
RANLIB='ranlib'
READLINE_LIB='-lreadline'
SCROLLKEEPER_CONFIG='/usr/bin/scrollkeeper-config'
SCROLLKEEPER_REQUIRED='0.3.8'
SET_MAKE=''
SHELL='/bin/bash'
STRIP='strip'
TERMCAP_LIB='-ltermcap'
UCB_CFLAGS=''
UCB_LDFLAGS=''
USE_NLS='yes'
VERSION='2.6.2'
WARN_CFLAGS='-Wall -Wmissing-prototypes '
WARN_CXXFLAGS='-g -O2 -Wall -Wno-unused '
XGETTEXT='/usr/bin/xgettext'
ac_ct_AR='ar'
ac_ct_CC='gcc'
ac_ct_CXX='g++'
ac_ct_F77=''
ac_ct_RANLIB='ranlib'
ac_ct_STRIP='strip'
am__fastdepCC_FALSE='#'
am__fastdepCC_TRUE=''
am__fastdepCXX_FALSE='#'
am__fastdepCXX_TRUE=''
am__include='include'
am__leading_dot='.'
am__quote=''
bindir='${exec_prefix}/bin'
build='i686-pc-linux-gnu'
build_alias=''
build_cpu='i686'
build_os='linux-gnu'
build_vendor='pc'
datadir='${prefix}/share'
exec_prefix='${prefix}'
host='i686-pc-linux-gnu'
host_alias=''
host_cpu='i686'
host_os='linux-gnu'
host_vendor='pc'
includedir='${prefix}/include'
infodir='${prefix}/info'
install_sh='/home/jordan/Desktop/gnome-games-2.6.2/install-sh'
libdir='${exec_prefix}/lib'
libexecdir='${exec_prefix}/libexec'
localstatedir='${prefix}/var'
mandir='${prefix}/man'
oldincludedir='/usr/include'
prefix='/home/jordan/Desktop/gnome-games-win32'
program_transform_name='s,x,x,'
sbindir='${exec_prefix}/sbin'
scoredir='${localstatedir}/games'
scores_group='games'
scores_user='games'
setgid='true'
sharedstatedir='${prefix}/com'
sysconfdir='${prefix}/etc'
target_alias=''

## ----------- ##
## confdefs.h. ##
## ----------- ##

#define ENABLE_NLS 1
#define GETTEXT_PACKAGE "gnome-games"
#define GNOME_ICONDIR "/home/jordan/Desktop/gnome-games-win32/share/pixmaps"
#define HAVE_BIND_TEXTDOMAIN_CODESET 1
#define HAVE_DCGETTEXT 1
#define HAVE_DLFCN_H 1
#define HAVE_GETTEXT 1
#define HAVE_INTTYPES_H 1
#define HAVE_LC_MESSAGES 1
#define HAVE_LIBM 1
#define HAVE_LOCALE_H 1
#define HAVE_MEMORY_H 1
#define HAVE_NGETTEXT 1
#define HAVE_STDBOOL_H 1
#define HAVE_STDINT_H 1
#define HAVE_STDLIB_H 1
#define HAVE_STRINGS_H 1
#define HAVE_STRING_H 1
#define HAVE_STRUCT_DIRECT 1
#define HAVE_SYS_DIR_H
#define HAVE_SYS_STAT_H 1
#define HAVE_SYS_TYPES_H 1
#define HAVE_UNISTD_H 1
#define HAVE__BOOL 1
#define PACKAGE "gnome-games"
#define PACKAGE_BUGREPORT "http://bugzilla.gnome.org/enter_bug.cgi?product=gnome-games"
#define PACKAGE_NAME "gnome-games"
#define PACKAGE_STRING "gnome-games 2.6.2"
#define PACKAGE_TARNAME "gnome-games"
#define PACKAGE_VERSION "2.6.2"
#define STDC_HEADERS 1
#define STDC_HEADERS 1
#define VERSION "2.6.2"
#endif
#ifdef __cplusplus
#include <stdlib.h>

configure: exit 0
```Any ideas?

---

### Post by Neo_The_User on 2009-03-09
Try running build-dep gnome-games and gnome-games-data or something. You seem to be missing headers.

---

### Post by dodle on 2009-03-09
This is what happens when I try to run those commands:```
laptop:~$ build-dep gnome-games
bash: build-dep: command not found
laptop:~$ sudo apt-get install build-dep
[sudo] password for jordan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-dep
laptop:~$ gnome-games-data
bash: gnome-games-data: command not found
laptop:~$ sudo apt-get install gnome-games-data
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-games-data is already the newest version.

```

---

### Post by Neo_The_User on 2009-03-09
...This is what I meant.

```

sudo apt-get build-dep gnome-games gnome-games-data gnome-cards-data

```

Be sure to install the glib dev tools as well and glibc dev tools, and glib2 dev tools. Use synaptic to find them. GTK 2.0 dev tools as well.

---

### Post by dodle on 2009-03-09
Sorry, I'm having trouble with my Broadcom B43 driver and can't connect to the internet with my Ubuntu machine.  I'll try your suggestion when I get this fixed.

[quote=Neo_The_User]...This is what I meant.
[/quote]

Please excuse my ignorance

---

