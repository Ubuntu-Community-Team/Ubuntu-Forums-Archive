---
title: "PHP help urgent"
date: 2010-08-13
forum: Programming Talk
---

### Post by gdubbs on 2010-08-13
Hi all 
 
Im haveing a issue here with this script adding peps to the database not sure why it dont
 
This is the config file for it 
 
[PHP]  //----------- added 20.07.2010-----------
function user_add($facebook,$curr_user)
{
  if( !$facebook )
  {
    return "testing...";
  }
  try
  {
    $q = "SELECT uid, first_name, last_name
          FROM user WHERE uid=".$curr_user;
    $rs = $facebook->api_client->fql_query($q);
    // Build an delimited list of users...
    if ( $rs )
    {
      $count = count($rs);
      for( $i=0; $i < $count; $i++ )
      {
        $u_id = intval($rs[$i]["uid"]);
        $f_name = trim($rs[$i]["first_name"]);
        $l_name = trim($rs[$i]["last_name"]);
        $name = $f_name." ".$l_name;
        break;
      }
    }
  }
  catch(Exception $ex)
  {
    echo $ex->getMessage();
  }
  if( isset($u_id) AND $u_id )
  {
    @db_execute("INSERT INTO `user` (`id` ,`name` )VALUES (".$u_id.", '".$name."');");
  }
}
function user_exists($curr_user)
{
  $sql = "SELECT id FROM `user` WHERE id=$curr_user;";
  $query = @db_execute($sql);
  if( $query )
  return mysql_num_rows($query);
}
?>
 [/PHP]
 
and this is the add user file 
 
[PHP]  <?php
require_once('facebook-client/facebook.php');
$facebook = new Facebook_new($api_key,$secret);
//echo "currr user: $curr_user<br>";
if( $facebook->get_loggedin_user() )
{
  $curr_user = $facebook->require_login();
  if( !user_exists($curr_user) )
  {
    @user_add($facebook,$curr_user);
    //echo "<br> added new user!";
  }
  else
  {
    //echo "<br>user already exists!";
  }
}
?> [/PHP]
 
 
im so lost any help would be great 
 
thanks

---

### Post by sahabcse on 2010-08-13
Did you check the apache and database error logs?

---

### Post by gdubbs on 2010-08-13
i get no errors thats why im not sure whats going on

---

### Post by surfer on 2010-08-13
did you install php5-cli (php command line interpreter) and try to run the script in a shell?

---

### Post by sahabcse on 2010-08-13
paste the o/p of phpinfo.

---

### Post by gdubbs on 2010-08-13
have no idea what you are talking about but i do have facebookapi_php5_restlib.php on the server it seems to work opnce or twice then dont work no more

---

### Post by gdubbs on 2010-08-13
> **sahabcse said:**
> paste the o/p of phpinfo.
 
 
 
not sure what you mean

---

### Post by Hellkeepa on 2010-08-13
HELLo!

Create a new file, and add the following bit to it:
[php]<?php
phpinfo ();
?>[/php]
And give us the output of it.

Also, remove the at (@) in front of the "db_execute ()" calls. It suppresses the error messages, which is most likely the reason why you're not seeing any.

Happy codin'!

---

### Post by gdubbs on 2010-08-13
[COLOR=#000000][CENTER][FONT=sans-serif][[IMG]http://ubuntuforums.org/eminem/info.php?=PHPE9568F34-D428-11d2-A769-00AA001ACF42[/IMG]]("http://www.php.net/")**PHP Version 5.2.9**


SystemLinux cameron.ourweb.net 2.6.18-92.el5 #1 SMP Tue Jun 10 18:51:06 EDT 2008 x86_64Build DateJun 25 2010 16:38:18Configure Command'./configure' '--enable-bcmath' '--enable-calendar' '--enable-dbase' '--enable-ftp' '--enable-gd-native-ttf' '--enable-libxml' '--enable-magic-quotes' '--enable-pdo=shared' '--enable-soap' '--enable-sockets' '--prefix=/usr' '--with-config-file-path=/usr/local/lib' '--with-config-file-scan-dir=/usr/local/lib/php.ini.d' '--with-curl=/opt/curlssl/' '--with-curlwrappers' '--with-freetype-dir=/usr' '--with-gd' '--with-gettext' '--with-imap=/opt/php_with_imap_client/' '--with-imap-ssl=/usr' '--with-jpeg-dir=/usr' '--with-kerberos' '--with-libdir=lib64' '--with-libxml-dir=/opt/xml2' '--with-libxml-dir=/opt/xml2/' '--with-mcrypt=/opt/libmcrypt/' '--with-mysql=/usr' '--with-mysql-sock=/var/lib/mysql/mysql.sock' '--with-openssl=/usr' '--with-openssl-dir=/usr' '--with-pcre-regex=/opt/pcre' '--with-pdo-mysql=shared' '--with-pdo-sqlite=shared' '--with-pic' '--with-png-dir=/usr' '--with-sqlite=shared' '--with-ttf' '--with-xpm-dir=/usr' '--with-zlib' '--with-zlib-dir=/usr'Server APICGIVirtual Directory SupportdisabledConfiguration File (php.ini) Path/usr/local/libLoaded Configuration File/usr/local/lib/php.iniScan this dir for additional .ini files/usr/local/lib/php.ini.dadditional .ini files parsed(none)PHP API20041225PHP Extension20060613Zend Extension220060519Debug BuildnoThread SafetydisabledZend Memory ManagerenabledIPv6 SupportenabledRegistered PHP Streamsphp, file, data, dict, ftp, ftps, http, https, imap, imaps, pop3, pop3s, rtsp, smtp, smtps, telnet, tftp, compress.zlibRegistered Stream Socket Transportstcp, udp, unix, udg, ssl, sslv3, sslv2, tlsRegistered Stream Filtersstring.rot13, string.toupper, string.tolower, string.strip_tags, convert.*, consumed, convert.iconv.*, zlib.*
[[IMG]http://ubuntuforums.org/eminem/info.php?=PHPE9568F35-D428-11d2-A769-00AA001ACF42[/IMG]]("http://www.zend.com/")This program makes use of the Zend Scripting Language Engine:
Zend Engine v2.2.0, Copyright (c) 1998-2009 Zend Technologies
    with the ionCube PHP Loader v3.3.20, Copyright (c) 2002-2010, by ionCube Ltd., and
    with Zend Optimizer v3.3.9, Copyright (c) 1998-2009, by Zend Technologies


**[PHP Credits]("http://ubuntuforums.org/eminem/info.php?=PHPB8B5F2A0-3C92-11d3-A3A9-4C7B08C10000")**

**Configuration**

**PHP Core**

DirectiveLocal ValueMaster Valueallow_call_time_pass_referenceOnOnallow_url_fopenOnOnallow_url_includeOffOffalways_populate_raw_post_dataOffOffarg_separator.input&&arg_separator.output&&asp_tagsOffOffauto_append_file*no value**no value*auto_globals_jitOnOnauto_prepend_file*no value**no value*browscap*no value**no value*default_charset*no value**no value*default_mimetypetext/htmltext/htmldefine_syslog_variablesOffOffdisable_classes*no value**no value*disable_functions*no value**no value*display_errorsSTDOUTSTDOUTdisplay_startup_errorsOffOffdoc_root*no value**no value*docref_ext*no value**no value*docref_root*no value**no value*enable_dlOnOnerror_append_string*no value**no value*error_logerror_logerror_logerror_prepend_string*no value**no value*error_reporting61356135expose_phpOnOnextension_dir/usr/local/lib/php/extensions/no-debug-non-zts-20060613/usr/local/lib/php/extensions/no-debug-non-zts-20060613file_uploadsOnOnhighlight.bg[COLOR=#FFFFFF]#FFFFFF[/COLOR][COLOR=#FFFFFF]#FFFFFF[/COLOR]highlight.comment[COLOR=#FF8000]#FF8000[/COLOR][COLOR=#FF8000]#FF8000[/COLOR]highlight.default[COLOR=#0000BB]#0000BB[/COLOR][COLOR=#0000BB]#0000BB[/COLOR]highlight.html[COLOR=#000000]#000000[/COLOR][COLOR=#000000]#000000[/COLOR]highlight.keyword[COLOR=#007700]#007700[/COLOR][COLOR=#007700]#007700[/COLOR]highlight.string[COLOR=#DD0000]#DD0000[/COLOR][COLOR=#DD0000]#DD0000[/COLOR]html_errorsOnOnignore_repeated_errorsOffOffignore_repeated_sourceOffOffignore_user_abortOffOffimplicit_flushOffOffinclude_path.:/usr/lib/php:/usr/local/lib/php.:/usr/lib/php:/usr/local/lib/phplog_errorsOnOnlog_errors_max_len10241024magic_quotes_gpcOnOnmagic_quotes_runtimeOffOffmagic_quotes_sybaseOffOffmail.force_extra_parameters*no value**no value*max_execution_time3030max_input_nesting_level6464max_input_time3535memory_limit72M72Mopen_basedir*no value**no value*output_buffering*no value**no value*output_handler*no value**no value*post_max_size8M8Mprecision1212realpath_cache_size16K16Krealpath_cache_ttl120120register_argc_argvOnOnregister_globalsOnOnregister_long_arraysOnOnreport_memleaksOnOnreport_zend_debugOnOnsafe_modeOffOffsafe_mode_exec_dir*no value**no value*safe_mode_gidOffOffsafe_mode_include_dir*no value**no value*sendmail_from*no value**no value*sendmail_path/usr/sbin/sendmail -t -i/usr/sbin/sendmail -t -iserialize_precision100100short_open_tagOnOnSMTPlocalhostlocalhostsmtp_port2525sql.safe_modeOffOfftrack_errorsOffOffunserialize_callback_func*no value**no value*upload_max_filesize20M20Mupload_tmp_dir*no value**no value*user_dir*no value**no value*variables_orderEGPCSEGPCSxmlrpc_error_number00xmlrpc_errorsOffOffy2k_complianceOnOnzend.ze1_compatibility_modeOffOff

**bcmath**

BCMath supportenabled

**calendar**

Calendar supportenabled

**cgi**

DirectiveLocal ValueMaster Valuecgi.check_shebang_line11cgi.fix_pathinfo11cgi.nph00cgi.rfc2616_headers00

**ctype**

ctype functionsenabled

**curl**

cURL supportenabledcURL Informationlibcurl/7.21.0 OpenSSL/0.9.8b zlib/1.2.3 libidn/0.6.5

**date**

date/time supportenabled"Olson" Timezone Database Version2009.1Timezone DatabaseinternalDefault timezoneAmerica/New_York
DirectiveLocal ValueMaster Valuedate.default_latitude31.766731.7667date.default_longitude35.233335.2333date.sunrise_zenith90.58333390.583333date.sunset_zenith90.58333390.583333date.timezone*no value**no value*

**dom**

DOM/XMLenabledDOM/XML API Version20031129libxml Version2.7.7HTML SupportenabledXPath SupportenabledXPointer SupportenabledSchema SupportenabledRelaxNG Supportenabled

**filter**

Input Validation and FilteringenabledRevision$Revision: 1.52.2.45 $
DirectiveLocal ValueMaster Valuefilter.defaultunsafe_rawunsafe_rawfilter.default_flags*no value**no value*

**ftp**

FTP supportenabled

**gd**

GD SupportenabledGD Versionbundled (2.0.34 compatible)FreeType SupportenabledFreeType Linkagewith freetypeFreeType Version2.2.1GIF Read SupportenabledGIF Create SupportenabledJPG SupportenabledPNG SupportenabledWBMP SupportenabledXPM SupportenabledXBM Supportenabled

**gettext**

GetText Supportenabled

**hash**

hash supportenabledHashing Enginesmd2 md4 md5 sha1 sha256 sha384 sha512 ripemd128 ripemd160 ripemd256 ripemd320 whirlpool tiger128,3 tiger160,3 tiger192,3 tiger128,4 tiger160,4 tiger192,4 snefru gost adler32 crc32 crc32b haval128,3 haval160,3 haval192,3 haval224,3 haval256,3 haval128,4 haval160,4 haval192,4 haval224,4 haval256,4 haval128,5 haval160,5 haval192,5 haval224,5 haval256,5

**iconv**

iconv supportenablediconv implementationglibciconv library version2.5
DirectiveLocal ValueMaster Valueiconv.input_encodingISO-8859-1ISO-8859-1iconv.internal_encodingISO-8859-1ISO-8859-1iconv.output_encodingISO-8859-1ISO-8859-1

**imap**

IMAP c-Client Version2007eSSL SupportenabledKerberos Supportenabled

**json**

json supportenabledjson version1.2.1

**libxml**

libXML supportactivelibXML Version2.7.7libXML streamsenabled

**magickwand**

MagickWand Backend LibraryImageMagickMagickWand Extension Version1.0.8ImageMagick supportenabledImageMagick versionImageMagick 6.4.8 2009-05-27 Q16 OpenMP [http://www.imagemagick.orgImageMagick](http://www.imagemagick.orgImageMagick) QuantumRange (MaxRGB)65535MagickWand supported image formatsA, AI, ART, ARW, AVI, AVS, B, BGR, BMP, BMP2, BMP3, BRF, BRG, C, CAPTION, CIN, CIP, CLIP, CMYK, CMYKA, CR2, CRW, CUR, CUT, DCM, DCR, DCX, DDS, DFONT, DNG, DOT, DPS, DPX, EPDF, EPI, EPS, EPS2, EPS3, EPSF, EPSI, ERF, FAX, FITS, FRACTAL, FTS, G, G3, GBR, GIF, GIF87, GRADIENT, GRAY, GRB, HISTOGRAM, HTM, HTML, ICB, ICO, ICON, INFO, INLINE, IPL, ISOBRL, JNG, JPEG, JPG, K, K25, KDC, LABEL, M, M2V, M4V, MAP, MAT, MATTE, MIFF, MNG, MONO, MOV, MP4, MPC, MPEG, MPG, MRW, MSL, MSVG, MTV, MVG, NEF, NULL, O, ORF, OTB, OTF, PAL, PALM, PAM, PATTERN, PBM, PCD, PCDS, PCL, PCT, PCX, PDB, PDF, PDFA, PEF, PFA, PFB, PFM, PGM, PICON, PICT, PIX, PJPEG, PLASMA, PNG, PNG24, PNG32, PNG8, PNM, PPM, PREVIEW, PS, PS2, PS3, PSD, PWP, R, RADIAL-GRADIENT, RAF, RAS, RBG, RGB, RGBA, RGBO, RLA, RLE, SCR, SCT, SFW, SGI, SHTML, SR2, SRF, STEGANO, SUN, SVG, SVGZ, TEXT, TGA, THUMBNAIL, TILE, TIM, TTC, TTF, TXT, UBRL, UIL, UYVY, VDA, VICAR, VID, VIFF, VST, WBMP, WMF, WMV, WMZ, WPG, X, X3F, XBM, XC, XCF, XPM, XPS, XV, XWD, Y, YCbCr, YCbCrA, YUV

**mcrypt**

mcrypt supportenabledVersion2.5.8Api No20021217Supported cipherscast-128 gost rijndael-128 twofish arcfour cast-256 loki97 rijndael-192 saferplus wake blowfish-compat des rijndael-256 serpent xtea blowfish enigma rc2 tripledesSupported modescbc cfb ctr ecb ncfb nofb ofb stream
DirectiveLocal ValueMaster Valuemcrypt.algorithms_dir*no value**no value*mcrypt.modes_dir*no value**no value*

**mysql**

MySQL SupportenabledActive Persistent Links0Active Links0Client API version5.0.91MYSQL_MODULE_TYPEexternalMYSQL_SOCKET/var/lib/mysql/mysql.sockMYSQL_INCLUDE-I/usr/include/mysqlMYSQL_LIBS-L/usr/lib64 -lmysqlclient
DirectiveLocal ValueMaster Valuemysql.allow_persistentOnOnmysql.connect_timeout6060mysql.default_host*no value**no value*mysql.default_password*no value**no value*mysql.default_port*no value**no value*mysql.default_socket*no value**no value*mysql.default_user*no value**no value*mysql.max_linksUnlimitedUnlimitedmysql.max_persistentUnlimitedUnlimitedmysql.trace_modeOffOff

**openssl**

OpenSSL supportenabledOpenSSL VersionOpenSSL 0.9.8e-fips-rhel5 01 Jul 2008

**pcre**

PCRE (Perl Compatible Regular Expressions) SupportenabledPCRE Library Version8.02 2010-03-19
DirectiveLocal ValueMaster Valuepcre.backtrack_limit100000100000pcre.recursion_limit100000100000

**PDO**

PDO supportenabledPDO driverssqlite, sqlite2, mysql

**pdo_mysql**

PDO Driver for MySQL, client library version5.0.91

**pdo_sqlite**

PDO Driver for SQLite 3.xenabledPECL Module version(bundled) 1.0.1 $Id: pdo_sqlite.c,v 1.10.2.6.2.4 2008/12/31 11:17:42 sebastian Exp $SQLite Library3.3.7

**posix**

Revision$Revision: 1.70.2.3.2.22 $

**Reflection**

ReflectionenabledVersion$Id: php_reflection.c,v 1.164.2.33.2.55 2008/12/31 11:17:42 sebastian Exp $

**session**

Session SupportenabledRegistered save handlersfiles user sqliteRegistered serializer handlersphp php_binary
DirectiveLocal ValueMaster Valuesession.auto_startOffOffsession.bug_compat_42OnOnsession.bug_compat_warnOnOnsession.cache_expire180180session.cache_limiternocachenocachesession.cookie_domain*no value**no value*session.cookie_httponlyOffOffsession.cookie_lifetime00session.cookie_path//session.cookie_secureOffOffsession.entropy_file*no value**no value*session.entropy_length00session.gc_divisor100100session.gc_maxlifetime14401440session.gc_probability11session.hash_bits_per_character44session.hash_function00session.namePHPSESSIDPHPSESSIDsession.referer_check*no value**no value*session.save_handlerfilesfilessession.save_path/tmp/tmpsession.serialize_handlerphpphpsession.use_cookiesOnOnsession.use_only_cookiesOffOffsession.use_trans_sid00

**SimpleXML**

Simplexml supportenabledRevision$Revision: 1.151.2.22.2.46 $Schema supportenabled

**soap**

Soap ClientenabledSoap Serverenabled
DirectiveLocal ValueMaster Valuesoap.wsdl_cache11soap.wsdl_cache_dir/tmp/tmpsoap.wsdl_cache_enabled11soap.wsdl_cache_limit55soap.wsdl_cache_ttl8640086400

**sockets**

Sockets Supportenabled

**SPL**

SPL supportenabledInterfacesCountable, OuterIterator, RecursiveIterator, SeekableIterator, SplObserver, SplSubjectClassesAppendIterator, ArrayIterator, ArrayObject, BadFunctionCallException, BadMethodCallException, CachingIterator, DirectoryIterator, DomainException, EmptyIterator, FilterIterator, InfiniteIterator, InvalidArgumentException, IteratorIterator, LengthException, LimitIterator, LogicException, NoRewindIterator, OutOfBoundsException, OutOfRangeException, OverflowException, ParentIterator, RangeException, RecursiveArrayIterator, RecursiveCachingIterator, RecursiveDirectoryIterator, RecursiveFilterIterator, RecursiveIteratorIterator, RecursiveRegexIterator, RegexIterator, RuntimeException, SimpleXMLIterator, SplFileInfo, SplFileObject, SplObjectStorage, SplTempFileObject, UnderflowException, UnexpectedValueException

**SQLite**

SQLite supportenabledPECL Module version2.0-dev $Id: sqlite.c,v 1.166.2.13.2.12 2008/12/31 11:17:44 sebastian Exp $SQLite Library2.8.17SQLite Encodingiso8859
DirectiveLocal ValueMaster Valuesqlite.assoc_case00

**standard**

Regex LibraryBundled library enabledDynamic Library SupportenabledPath to sendmail/usr/sbin/sendmail -t -i
DirectiveLocal ValueMaster Valueassert.active11assert.bail00assert.callback*no value**no value*assert.quiet_eval00assert.warning11auto_detect_line_endings00default_socket_timeout6060safe_mode_allowed_env_varsPHP_PHP_safe_mode_protected_env_varsLD_LIBRARY_PATHLD_LIBRARY_PATHurl_rewriter.tagsa=href,area=href,frame=src,input=src,form=,fieldset=a=href,area=href,frame=src,input=src,form=,fieldset=user_agent*no value**no value*

**tokenizer**

Tokenizer Supportenabled

**xml**

XML SupportactiveXML Namespace Supportactivelibxml2 Version2.7.7

**xmlreader**

XMLReaderenabled

**xmlwriter**

XMLWriterenabled

**Zend Optimizer**

Optimization Pass 1enabledOptimization Pass 2enabledOptimization Pass 3enabledOptimization Pass 4enabledOptimization Pass 9enabledZend LoaderenabledLicense Path*no value*Obfuscation level3

**zlib**

ZLib SupportenabledStream Wrapper supportcompress.zlib://Stream Filter supportzlib.inflate, zlib.deflateCompiled Version1.2.3Linked Version1.2.3
DirectiveLocal ValueMaster Valuezlib.output_compressionOffOffzlib.output_compression_level-1-1zlib.output_handler*no value**no value*

**Additional Modules**

Module NamedbaseionCube Loader

**Environment**

VariableValueDOCUMENT_ROOT/home/immortal/public_htmlGATEWAY_INTERFACECGI/1.1HTTP_ACCEPTapplication/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5HTTP_ACCEPT_CHARSETISO-8859-1,utf-8;q=0.7,*;q=0.3HTTP_ACCEPT_ENCODINGgzip,deflate,sdchHTTP_ACCEPT_LANGUAGEen-US,en;q=0.8HTTP_CONNECTIONkeep-aliveHTTP_COOKIE__utma=248857119.597181198.1274767456.1281511484.1281519010.23; __utmz=248857119.1281519010.23.4.utmccn=(referral)|utmcsr=facebook.com|utmcct=/l.php|utmcmd=referralHTTP_HOSTimmortalbattle.comHTTP_USER_AGENTMozilla/5.0 (Windows; U; Windows NT 6.0; en-US) AppleWebKit/533.4 (KHTML, like Gecko) Chrome/5.0.375.126 Safari/533.4PATH/bin:/usr/binQUERY_STRING*no value*REDIRECT_STATUS200REMOTE_ADDR72.133.45.17REMOTE_PORT52290REQUEST_METHODGETREQUEST_URI/eminem/info.phpSCRIPT_FILENAME/home/immortal/public_html/eminem/info.phpSCRIPT_NAME/eminem/info.phpSERVER_ADDR216.236.255.10SERVER_ADMINwebmaster@immortalbattle.comSERVER_NAMEimmortalbattle.comSERVER_PORT80SERVER_PROTOCOLHTTP/1.1SERVER_SIGNATURE*no value*SERVER_SOFTWAREApacheUNIQUE_ID1o4huNjs-woAACEhE-EAAAA0

**PHP Variables**

VariableValuePHP_SELF/eminem/info.php_REQUEST["__utma"]248857119.597181198.1274767456.1281511484.1281519010.23_REQUEST["__utmz"]248857119.1281519010.23.4.utmccn=(referral)|utmcsr=facebook.com|utmcct=/l.php|utmcmd=referral_COOKIE["__utma"]248857119.597181198.1274767456.1281511484.1281519010.23_COOKIE["__utmz"]248857119.1281519010.23.4.utmccn=(referral)|utmcsr=facebook.com|utmcct=/l.php|utmcmd=referral_SERVER["DOCUMENT_ROOT"]/home/immortal/public_html_SERVER["GATEWAY_INTERFACE"]CGI/1.1_SERVER["HTTP_ACCEPT"]application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5_SERVER["HTTP_ACCEPT_CHARSET"]ISO-8859-1,utf-8;q=0.7,*;q=0.3_SERVER["HTTP_ACCEPT_ENCODING"]gzip,deflate,sdch_SERVER["HTTP_ACCEPT_LANGUAGE"]en-US,en;q=0.8_SERVER["HTTP_CONNECTION"]keep-alive_SERVER["HTTP_COOKIE"]__utma=248857119.597181198.1274767456.1281511484.1281519010.23; __utmz=248857119.1281519010.23.4.utmccn=(referral)|utmcsr=facebook.com|utmcct=/l.php|utmcmd=referral_SERVER["HTTP_HOST"]immortalbattle.com_SERVER["HTTP_USER_AGENT"]Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US) AppleWebKit/533.4 (KHTML, like Gecko) Chrome/5.0.375.126 Safari/533.4_SERVER["PATH"]/bin:/usr/bin_SERVER["QUERY_STRING"]*no value*_SERVER["REDIRECT_STATUS"]200_SERVER["REMOTE_ADDR"]72.133.45.17_SERVER["REMOTE_PORT"]52290_SERVER["REQUEST_METHOD"]GET_SERVER["REQUEST_URI"]/eminem/info.php_SERVER["SCRIPT_FILENAME"]/home/immortal/public_html/eminem/info.php_SERVER["SCRIPT_NAME"]/eminem/info.php_SERVER["SERVER_ADDR"]216.236.255.10_SERVER["SERVER_ADMIN"]webmaster@immortalbattle.com_SERVER["SERVER_NAME"]immortalbattle.com_SERVER["SERVER_PORT"]80_SERVER["SERVER_PROTOCOL"]HTTP/1.1_SERVER["SERVER_SIGNATURE"]*no value*_SERVER["SERVER_SOFTWARE"]Apache_SERVER["UNIQUE_ID"]1o4huNjs-woAACEhE-EAAAA0_SERVER["PHP_SELF"]/eminem/info.php_SERVER["REQUEST_TIME"]1281694855_SERVER["argv"]Array()_SERVER["argc"]0_ENV["DOCUMENT_ROOT"]/home/immortal/public_html_ENV["GATEWAY_INTERFACE"]CGI/1.1_ENV["HTTP_ACCEPT"]application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5_ENV["HTTP_ACCEPT_CHARSET"]ISO-8859-1,utf-8;q=0.7,*;q=0.3_ENV["HTTP_ACCEPT_ENCODING"]gzip,deflate,sdch_ENV["HTTP_ACCEPT_LANGUAGE"]en-US,en;q=0.8_ENV["HTTP_CONNECTION"]keep-alive_ENV["HTTP_COOKIE"]__utma=248857119.597181198.1274767456.1281511484.1281519010.23; __utmz=248857119.1281519010.23.4.utmccn=(referral)|utmcsr=facebook.com|utmcct=/l.php|utmcmd=referral_ENV["HTTP_HOST"]immortalbattle.com_ENV["HTTP_USER_AGENT"]Mozilla/5.0 (Windows; U; Windows NT 6.0; en-US) AppleWebKit/533.4 (KHTML, like Gecko) Chrome/5.0.375.126 Safari/533.4_ENV["PATH"]/bin:/usr/bin_ENV["QUERY_STRING"]*no value*_ENV["REDIRECT_STATUS"]200_ENV["REMOTE_ADDR"]72.133.45.17_ENV["REMOTE_PORT"]52290_ENV["REQUEST_METHOD"]GET_ENV["REQUEST_URI"]/eminem/info.php_ENV["SCRIPT_FILENAME"]/home/immortal/public_html/eminem/info.php_ENV["SCRIPT_NAME"]/eminem/info.php_ENV["SERVER_ADDR"]216.236.255.10_ENV["SERVER_ADMIN"]webmaster@immortalbattle.com_ENV["SERVER_NAME"]immortalbattle.com_ENV["SERVER_PORT"]80_ENV["SERVER_PROTOCOL"]HTTP/1.1_ENV["SERVER_SIGNATURE"]*no value*_ENV["SERVER_SOFTWARE"]Apache_ENV["UNIQUE_ID"]1o4huNjs-woAACEhE-EAAAA0[/FONT][/CENTER][/COLOR]

---

### Post by gdubbs on 2010-08-13
and i removed the @ and still no message but i get null so its not working its not getting logged in user is what i think the issue is

---

