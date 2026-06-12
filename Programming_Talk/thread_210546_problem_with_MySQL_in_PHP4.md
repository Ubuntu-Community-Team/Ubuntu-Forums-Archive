---
title: "problem with MySQL in PHP4"
date: 2006-07-07
forum: Programming Talk
---

### Post by Dooq on 2006-07-07
Hello everyone,
I installed the folowing:
apache2
php4
mysql-server
libapache2-mod-auth-mysql
php4-mysql
phpmyadmin

put when I try to run my application I get this message:
[PHP]Fatal error: Call to undefined function mysql_connect()[/PHP]

How can I fix that ?

I hade been change my /var/www floder permission from root user to my corrent user to edit my project easily I dont think that's the problem !!

this is my phpinfo() result - seems MYSQL not support ?? Whay ? -

[PHP]
PHP Version 5.1.2

System 	Linux Dooq-laptop 2.6.15-25-386 #1 PREEMPT Wed Jun 14 11:25:49 UTC 2006 i686
Build Date 	May 18 2006 04:50:34
Server API 	Apache 2.0 Handler
Virtual Directory Support 	disabled
Configuration File (php.ini) Path 	/etc/php5/apache2/php.ini
PHP API 	20041225
PHP Extension 	20050922
Zend Extension 	220051025
Debug Build 	no
Thread Safety 	disabled
Zend Memory Manager 	enabled
IPv6 Support 	enabled
Registered PHP Streams 	php, file, http, ftp, compress.bzip2, compress.zlib, https, ftps
Registered Stream Socket Transports 	tcp, udp, unix, udg, ssl, sslv3, sslv2, tls
Registered Stream Filters 	string.rot13, string.toupper, string.tolower, string.strip_tags, convert.*, convert.iconv.*, bzip2.*, zlib.*

Zend logo This program makes use of the Zend Scripting Language Engine:
Zend Engine v2.1.0, Copyright (c) 1998-2006 Zend Technologies

PHP Credits
Configuration
PHP Core
Directive	Local Value	Master Value
allow_call_time_pass_reference	On	On
allow_url_fopen	On	On
always_populate_raw_post_data	Off	Off
arg_separator.input	&	&
arg_separator.output	&	&
asp_tags	Off	Off
auto_append_file	no value	no value
auto_globals_jit	On	On
auto_prepend_file	no value	no value
browscap	no value	no value
default_charset	no value	no value
default_mimetype	text/html	text/html
define_syslog_variables	Off	Off
disable_classes	no value	no value
disable_functions	no value	no value
display_errors	On	On
display_startup_errors	Off	Off
doc_root	no value	no value
docref_ext	no value	no value
docref_root	no value	no value
enable_dl	On	On
error_append_string	no value	no value
error_log	no value	no value
error_prepend_string	no value	no value
error_reporting	2039	2039
expose_php	On	On
extension_dir	/usr/lib/php5/20051025	/usr/lib/php5/20051025
file_uploads	On	On
highlight.bg	#FFFFFF	#FFFFFF
highlight.comment	#FF8000	#FF8000
highlight.default	#0000BB	#0000BB
highlight.html	#000000	#000000
highlight.keyword	#007700	#007700
highlight.string	#DD0000	#DD0000
html_errors	On	On
ignore_repeated_errors	Off	Off
ignore_repeated_source	Off	Off
ignore_user_abort	Off	Off
implicit_flush	Off	Off
include_path	.:/usr/share/php:/usr/share/pear	.:/usr/share/php:/usr/share/pear
log_errors	Off	Off
log_errors_max_len	1024	1024
magic_quotes_gpc	On	On
magic_quotes_runtime	Off	Off
magic_quotes_sybase	Off	Off
mail.force_extra_parameters	no value	no value
max_execution_time	30	30
max_input_time	60	60
memory_limit	8M	8M
open_basedir	no value	no value
output_buffering	no value	no value
output_handler	no value	no value
post_max_size	8M	8M
precision	12	12
realpath_cache_size	16K	16K
realpath_cache_ttl	120	120
register_argc_argv	On	On
register_globals	Off	Off
register_long_arrays	On	On
report_memleaks	On	On
report_zend_debug	On	On
safe_mode	Off	Off
safe_mode_exec_dir	no value	no value
safe_mode_gid	Off	Off
safe_mode_include_dir	no value	no value
sendmail_from	no value	no value
sendmail_path	/usr/sbin/sendmail -t -i 	/usr/sbin/sendmail -t -i 
serialize_precision	100	100
short_open_tag	On	On
SMTP	localhost	localhost
smtp_port	25	25
sql.safe_mode	Off	Off
track_errors	Off	Off
unserialize_callback_func	no value	no value
upload_max_filesize	2M	2M
upload_tmp_dir	no value	no value
user_dir	no value	no value
variables_order	EGPCS	EGPCS
xmlrpc_error_number	0	0
xmlrpc_errors	Off	Off
y2k_compliance	On	On
zend.ze1_compatibility_mode	Off	Off

apache2handler
Apache Version 	Apache/2.0.55 (Ubuntu) PHP/5.1.2
Apache API Version 	20020903
Server Administrator 	webmaster@localhost
Hostname:Port 	127.0.1.1:0
User/Group 	www-data(33)/33
Max Requests 	Per Child: 0 - Keep Alive: on - Max Per Connection: 100
Timeouts 	Connection: 300 - Keep-Alive: 15
Virtual Server 	Yes
Server Root 	/etc/apache2
Loaded Modules 	core mod_access mod_auth mod_log_config mod_logio mod_env mod_setenvif prefork http_core mod_mime mod_status mod_autoindex mod_negotiation mod_dir mod_alias mod_so mod_cgi mod_php5 mod_userdir

Directive	Local Value	Master Value
engine	1	1
last_modified	0	0
xbithack	0	0

Apache Environment
Variable	Value
HTTP_HOST 	localhost
HTTP_USER_AGENT 	Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.4) Gecko/20060608 Ubuntu/dapper-security Firefox/1.5.0.4
HTTP_ACCEPT 	text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
HTTP_ACCEPT_LANGUAGE 	en-us,en;q=0.5
HTTP_ACCEPT_ENCODING 	gzip,deflate
HTTP_ACCEPT_CHARSET 	ISO-8859-1,utf-8;q=0.7,*;q=0.7
HTTP_KEEP_ALIVE 	300
HTTP_CONNECTION 	keep-alive
HTTP_REFERER 	http://localhost/
PATH 	/usr/local/bin:/usr/bin:/bin
SERVER_SIGNATURE 	<address>Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at localhost Port 80</address>
SERVER_SOFTWARE 	Apache/2.0.55 (Ubuntu) PHP/5.1.2
SERVER_NAME 	localhost
SERVER_ADDR 	127.0.0.1
SERVER_PORT 	80
REMOTE_ADDR 	127.0.0.1
DOCUMENT_ROOT 	/var/www
SERVER_ADMIN 	webmaster@localhost
SCRIPT_FILENAME 	/var/www/Test.php
REMOTE_PORT 	39193
GATEWAY_INTERFACE 	CGI/1.1
SERVER_PROTOCOL 	HTTP/1.1
REQUEST_METHOD 	GET
QUERY_STRING 	no value
REQUEST_URI 	/Test.php
SCRIPT_NAME 	/Test.php

HTTP Headers Information
HTTP Request Headers
HTTP Request 	GET /Test.php HTTP/1.1
Host 	localhost
User-Agent 	Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.4) Gecko/20060608 Ubuntu/dapper-security Firefox/1.5.0.4
Accept 	text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
Accept-Language 	en-us,en;q=0.5
Accept-Encoding 	gzip,deflate
Accept-Charset 	ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive 	300
Connection 	keep-alive
Referer 	http://localhost/
HTTP Response Headers
X-Powered-By 	PHP/5.1.2
Keep-Alive 	timeout=15, max=99
Connection 	Keep-Alive
Transfer-Encoding 	chunked
Content-Type 	text/html; charset=UTF-8

bcmath
BCMath support 	enabled

bz2
BZip2 Support 	Enabled
Stream Wrapper support 	compress.bz2://
Stream Filter support 	bzip2.decompress, bzip2.compress
BZip2 Version 	1.0.3, 15-Feb-2005

calendar
Calendar support 	enabled

ctype
ctype functions 	enabled

date
date/time support 	enabled
Timezone Database Version 	2005.18
Timezone Database 	internal
Default timezone 	Asia/Riyadh

Directive	Local Value	Master Value
date.default_latitude	31.7667	31.7667
date.default_longitude	35.2333	35.2333
date.sunrise_zenith	90.583333	90.583333
date.sunset_zenith	90.583333	90.583333
date.timezone	no value	no value

dba
DBA support 	enabled
Supported handlers 	gdbm cdb cdb_make db4 inifile flatfile

dom
DOM/XML 	enabled
DOM/XML API Version 	20031129
libxml Version 	2.6.24
HTML Support 	enabled
XPath Support 	enabled
XPointer Support 	enabled
Schema Support 	enabled
RelaxNG Support 	enabled

exif
EXIF Support 	enabled
EXIF Version 	1.4 $Id: exif.c,v 1.173.2.4 2006/01/01 12:50:06 sniper Exp $
Supported EXIF Version 	0220
Supported filetypes 	JPEG,TIFF

ftp
FTP support 	enabled

gd
GD Support 	enabled
GD Version 	2.0 or higher
FreeType Support 	enabled
FreeType Linkage 	with freetype
FreeType Version 	2.1.10
T1Lib Support 	enabled
GIF Read Support 	enabled
GIF Create Support 	enabled
JPG Support 	enabled
PNG Support 	enabled
WBMP Support 	enabled

gettext
GetText Support 	enabled

hash
hash support	enabled
Hashing Engines	md4 md5 sha1 sha256 sha384 sha512 ripemd128 ripemd160 whirlpool tiger128,3 tiger160,3 tiger192,3 tiger128,4 tiger160,4 tiger192,4 snefru gost adler32 crc32 crc32b haval128,3 haval160,3 haval192,3 haval224,3 haval256,3 haval128,4 haval160,4 haval192,4 haval224,4 haval256,4 haval128,5 haval160,5 haval192,5 haval224,5 haval256,5

iconv
iconv support 	enabled
iconv implementation 	glibc
iconv library version 	2.3.6

Directive	Local Value	Master Value
iconv.input_encoding	ISO-8859-1	ISO-8859-1
iconv.internal_encoding	ISO-8859-1	ISO-8859-1
iconv.output_encoding	ISO-8859-1	ISO-8859-1

libxml
libXML support 	active
libXML Version 	2.6.24
libXML streams 	enabled

mbstring
Multibyte Support 	enabled
Multibyte string engine 	libmbfl
Multibyte (japanese) regex support 	enabled
Multibyte regex (oniguruma) version 	3.7.1

mbstring extension makes use of "streamable kanji code filter and converter", which is distributed under the GNU Lesser General Public License version 2.1.

Directive	Local Value	Master Value
mbstring.detect_order	no value	no value
mbstring.encoding_translation	Off	Off
mbstring.func_overload	0	0
mbstring.http_input	pass	pass
mbstring.http_output	pass	pass
mbstring.internal_encoding	ISO-8859-1	no value
mbstring.language	neutral	neutral
mbstring.strict_detection	Off	Off
mbstring.substitute_character	no value	no value

mcrypt
mcrypt support	enabled
Version 	2.5.7
Api No 	20021217
Supported ciphers 	cast-128 gost rijndael-128 twofish arcfour cast-256 loki97 rijndael-192 saferplus wake blowfish-compat des rijndael-256 serpent xtea blowfish enigma rc2 tripledes
Supported modes 	cbc cfb ctr ecb ncfb nofb ofb stream

Directive	Local Value	Master Value
mcrypt.algorithms_dir	no value	no value
mcrypt.modes_dir	no value	no value

mime_magic
mime_magic support	enabled

Directive	Local Value	Master Value
mime_magic.debug	Off	Off
mime_magic.magicfile	/usr/share/file/magic.mime	/usr/share/file/magic.mime

openssl
OpenSSL support 	enabled
OpenSSL Version 	OpenSSL 0.9.8a 11 Oct 2005

pcre
PCRE (Perl Compatible Regular Expressions) Support 	enabled
PCRE Library Version 	6.4 05-Sep-2005

posix
Revision 	$Revision: 1.70.2.3 $

Reflection
Reflection	enabled
Version 	$Id: php_reflection.c,v 1.164.2.17 2006/01/01 12:50:12 sniper Exp $

session
Session Support 	enabled
Registered save handlers 	files user
Registered serializer handlers 	php php_binary wddx

Directive	Local Value	Master Value
session.auto_start	Off	Off
session.bug_compat_42	On	On
session.bug_compat_warn	On	On
session.cache_expire	180	180
session.cache_limiter	nocache	nocache
session.cookie_domain	no value	no value
session.cookie_lifetime	0	0
session.cookie_path	/	/
session.cookie_secure	Off	Off
session.entropy_file	no value	no value
session.entropy_length	0	0
session.gc_divisor	100	100
session.gc_maxlifetime	1440	1440
session.gc_probability	0	0
session.hash_bits_per_character	4	4
session.hash_function	0	0
session.name	PHPSESSID	PHPSESSID
session.referer_check	no value	no value
session.save_handler	files	files
session.save_path	/var/lib/php5	/var/lib/php5
session.serialize_handler	php	php
session.use_cookies	On	On
session.use_only_cookies	Off	Off
session.use_trans_sid	0	0

shmop
shmop support 	enabled

SimpleXML
Simplexml support	enabled
Revision 	$Revision: 1.151.2.10 $
Schema support 	enabled

soap
Soap Client 	enabled
Soap Server 	enabled

Directive	Local Value	Master Value
soap.wsdl_cache_dir	/tmp	/tmp
soap.wsdl_cache_enabled	1	1
soap.wsdl_cache_ttl	86400	86400

sockets
Sockets Support 	enabled

SPL
SPL support	enabled
Interfaces 	Countable, OuterIterator, RecursiveIterator, SeekableIterator, SplObserver, SplSubject
Classes 	AppendIterator, ArrayIterator, ArrayObject, BadFunctionCallException, BadMethodCallException, CachingIterator, DirectoryIterator, DomainException, EmptyIterator, FilterIterator, InfiniteIterator, InvalidArgumentException, IteratorIterator, LengthException, LimitIterator, LogicException, NoRewindIterator, OutOfBoundsException, OutOfRangeException, OverflowException, ParentIterator, RangeException, RecursiveArrayIterator, RecursiveCachingIterator, RecursiveDirectoryIterator, RecursiveFilterIterator, RecursiveIteratorIterator, RuntimeException, SimpleXMLIterator, SplFileInfo, SplFileObject, SplObjectStorage, SplTempFileObject, UnderflowException, UnexpectedValueException

standard
Regex Library 	Bundled library enabled
Dynamic Library Support 	enabled
Path to sendmail 	/usr/sbin/sendmail -t -i

Directive	Local Value	Master Value
assert.active	1	1
assert.bail	0	0
assert.callback	no value	no value
assert.quiet_eval	0	0
assert.warning	1	1
auto_detect_line_endings	0	0
default_socket_timeout	60	60
safe_mode_allowed_env_vars	PHP_	PHP_
safe_mode_protected_env_vars	LD_LIBRARY_PATH	LD_LIBRARY_PATH
url_rewriter.tags	a=href,area=href,frame=src,input=src,form=,fieldset=	a=href,area=href,frame=src,input=src,form=,fieldset=
user_agent	no value	no value

sysvmsg
sysvmsg support 	enabled
Revision 	$Revision: 1.20.2.3 $

tokenizer
Tokenizer Support 	enabled

wddx
WDDX Support	enabled
WDDX Session Serializer 	enabled

xml
XML Support 	active
XML Namespace Support 	active
libxml2 Version 	2.6.24

xmlreader
XMLReader 	enabled

xmlwriter
XMLWriter 	enabled

zlib
ZLib Support 	enabled
Stream Wrapper support 	compress.zlib://
Stream Filter support 	zlib.inflate, zlib.deflate
Compiled Version 	1.2.3
Linked Version 	1.2.3

Directive	Local Value	Master Value
zlib.output_compression	Off	Off
zlib.output_compression_level	-1	-1
zlib.output_handler	no value	no value

Additional Modules
Module Name
filepro
sysvsem
sysvshm

Environment
Variable	Value
PATH 	/usr/local/bin:/usr/bin:/bin
PWD 	/
LANG 	C
SHLVL 	1
_ 	/usr/sbin/apache2

PHP Variables
Variable	Value
_SERVER["HTTP_HOST"]	localhost
_SERVER["HTTP_USER_AGENT"]	Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.0.4) Gecko/20060608 Ubuntu/dapper-security Firefox/1.5.0.4
_SERVER["HTTP_ACCEPT"]	text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
_SERVER["HTTP_ACCEPT_LANGUAGE"]	en-us,en;q=0.5
_SERVER["HTTP_ACCEPT_ENCODING"]	gzip,deflate
_SERVER["HTTP_ACCEPT_CHARSET"]	ISO-8859-1,utf-8;q=0.7,*;q=0.7
_SERVER["HTTP_KEEP_ALIVE"]	300
_SERVER["HTTP_CONNECTION"]	keep-alive
_SERVER["HTTP_REFERER"]	http://localhost/
_SERVER["PATH"]	/usr/local/bin:/usr/bin:/bin
_SERVER["SERVER_SIGNATURE"]	<address>Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at localhost Port 80</address>
_SERVER["SERVER_SOFTWARE"]	Apache/2.0.55 (Ubuntu) PHP/5.1.2
_SERVER["SERVER_NAME"]	localhost
_SERVER["SERVER_ADDR"]	127.0.0.1
_SERVER["SERVER_PORT"]	80
_SERVER["REMOTE_ADDR"]	127.0.0.1
_SERVER["DOCUMENT_ROOT"]	/var/www
_SERVER["SERVER_ADMIN"]	webmaster@localhost
_SERVER["SCRIPT_FILENAME"]	/var/www/Test.php
_SERVER["REMOTE_PORT"]	39193
_SERVER["GATEWAY_INTERFACE"]	CGI/1.1
_SERVER["SERVER_PROTOCOL"]	HTTP/1.1
_SERVER["REQUEST_METHOD"]	GET
_SERVER["QUERY_STRING"]	no value
_SERVER["REQUEST_URI"]	/Test.php
_SERVER["SCRIPT_NAME"]	/Test.php
_SERVER["PHP_SELF"]	/Test.php
_SERVER["REQUEST_TIME"]	1152250672
_SERVER["argv"]	

Array
(
)

_SERVER["argc"]	0
_ENV["PATH"]	/usr/local/bin:/usr/bin:/bin
_ENV["PWD"]	/
_ENV["LANG"]	C
_ENV["SHLVL"]	1
_ENV["_"]	/usr/sbin/apache2

PHP License

This program is free software; you can redistribute it and/or modify it under the terms of the PHP License as published by the PHP Group and included in the distribution in the file: LICENSE

This program is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

If you did not receive a copy of the PHP license, or have any questions about PHP licensing, please contact license@php.net. 
[/PHP]

---

### Post by Dooq on 2006-07-07
I installed PHP4 and he said in phpinfo : PHP Version 5.1.2 
How could that been ?

---

### Post by ifokkema on 2006-07-08
> **Dooq said:**
> I installed PHP4 and he said in phpinfo : PHP Version 5.1.2 
How could that been ?

Hi,

Run this to check out what you've got installed right now:
```
dpkg -l \*php\* \*mysql\* \*apache\* |grep ii
```
return the output, and we'll have a look.

---

### Post by Dooq on 2006-07-16
Thank you ifokkema,
I didnt install the php5-mysql because I've PHP4
But after I installed it every thing work.
The PHP version I using now is PHP5.
Thanks again,

---

