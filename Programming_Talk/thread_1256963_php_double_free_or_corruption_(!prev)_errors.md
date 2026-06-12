---
title: "php: double free or corruption (!prev) errors"
date: 2009-09-03
forum: Programming Talk
---

### Post by rogerr on 2009-09-03
Hi,
 I would like to mention 2 problems here:

Problem #1:

 I have a file called test.php.
 If I run
> php test.php everything goes fine.  But if I run 
> php test.php | head -10I get the following huge error:
```

*** glibc detected *** php: double free or corruption (!prev): 0x08e98710 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb78b6454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb78b84b6]
/lib/tls/i686/cmov/libc.so.6(fclose+0x144)[0xb78a6064]
php[0x82a8408]
php(_php_stream_free+0xc7)[0x82a2cb7]
php[0x82a2f18]
php(list_entry_destructor+0xa3)[0x82e3c33]
php[0x82e0904]
php(zend_hash_graceful_reverse_destroy+0x27)[0x82e0bc7]
php(zend_destroy_rsrc_list+0x1d)[0x82e3a7d]
php(zend_deactivate+0xaf)[0x82d5d9f]
php(php_request_shutdown+0x186)[0x828cbe6]
php(main+0x843)[0x836a8d3]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb785d685]
php[0x808f6a1]
======= Memory map: ========
08048000-08589000 r-xp 00000000 08:01 270882     /usr/bin/php5
08589000-085c2000 rw-p 00540000 08:01 270882     /usr/bin/php5
085c2000-085c7000 rw-p 085c2000 00:00 0
08d30000-09460000 rw-p 08d30000 00:00 0          [heap]
b7000000-b7021000 rw-p b7000000 00:00 0
b7021000-b7100000 ---p b7021000 00:00 0
b711a000-b7127000 r-xp 00000000 08:01 155856     /lib/libgcc_s.so.1
b7127000-b7128000 r--p 0000c000 08:01 155856     /lib/libgcc_s.so.1
b7128000-b7129000 rw-p 0000d000 08:01 155856     /lib/libgcc_s.so.1
b7129000-b720a000 r--p 00000000 08:01 278931     /usr/lib/locale/en_US.utf8/LC_COLLATE
b720a000-b7214000 r-xp 00000000 08:01 164659     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7214000-b7215000 r--p 00009000 08:01 164659     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7215000-b7216000 rw-p 0000a000 08:01 164659     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7216000-b721c000 r-xp 00000000 08:01 311800     /usr/lib/php5/20060613+lfs/pdo_mysql.so
b721c000-b721d000 rw-p 00005000 08:01 311800     /usr/lib/php5/20060613+lfs/pdo_mysql.so
b721d000-b7230000 r-xp 00000000 08:01 311804     /usr/lib/php5/20060613+lfs/pdo.so
b7230000-b7232000 rw-p 00013000 08:01 311804     /usr/lib/php5/20060613+lfs/pdo.so
b7232000-b7248000 r-xp 00000000 08:01 311799     /usr/lib/php5/20060613+lfs/mysqli.so
b7248000-b724a000 rw-p 00016000 08:01 311799     /usr/lib/php5/20060613+lfs/mysqli.so
b724a000-b73e8000 r-xp 00000000 08:01 272050     /usr/lib/libmysqlclient.so.15.0.0
b73e8000-b73e9000 ---p 0019e000 08:01 272050     /usr/lib/libmysqlclient.so.15.0.0
b73e9000-b73ec000 r--p 0019e000 08:01 272050     /usr/lib/libmysqlclient.so.15.0.0
b73ec000-b742c000 rw-p 001a1000 08:01 272050     /usr/lib/libmysqlclient.so.15.0.0
b742c000-b742d000 rw-p b742c000 00:00 0
b742d000-b7437000 r-xp 00000000 08:01 311798     /usr/lib/php5/20060613+lfs/mysql.so
b7437000-b7438000 rw-p 0000a000 08:01 311798     /usr/lib/php5/20060613+lfs/mysql.so
b7438000-b7442000 r-xp 00000000 08:01 155874     /lib/libpam.so.0.81.12
b7442000-b7443000 r--p 00009000 08:01 155874     /lib/libpam.so.0.81.12
b7443000-b7444000 rw-p 0000a000 08:01 155874     /lib/libpam.so.0.81.12
b7444000-b754e000 r-xp 00000000 08:01 462236     /usr/lib/libc-client.so.2007b.0
b754e000-b754f000 r--p 0010a000 08:01 462236     /usr/lib/libc-client.so.2007b.0
b754f000-b7555000 rw-p 0010b000 08:01 462236     /usr/lib/libc-client.so.2007b.0
b7555000-b7556000 rw-p b7555000 00:00 0
b7556000-b756c000 r-xp 00000000 08:01 314818     /usr/lib/php5/20060613+lfs/imap.so
b756c000-b756d000 r--p 00015000 08:01 314818     /usr/lib/php5/20060613+lfs/imap.so
b756d000-b756e000 rw-p 00016000 08:01 314818     /usr/lib/php5/20060613+lfs/imap.so
b756e000-b7571000 r-xp 00000000 08:01 155858     /lib/libgpg-error.so.0.3.0
b7571000-b7572000 rw-p 00002000 08:01 155858     /lib/libgpg-error.so.0.3.0
b7572000-b75d8000 r-xp 00000000 08:01 155857     /lib/libgcrypt.so.11.4.4
b75d8000-b75d9000 r--p 00065000 08:01 155857     /lib/libgcrypt.so.11.4.4
b75d9000-b75db000 rw-p 00066000 08:01 155857     /lib/libgcrypt.so.11.4.4
b75db000-b75eb000 r-xp 00000000 08:01 271097     /usr/lib/libtasn1.so.3.0.15
b75eb000-b75ed000 rw-p 0000f000 08:01 271097     /usr/lib/libtasn1.so.3.0.15
b75ed000-b7684000 r-xp 00000000 08:01 270496     /usr/lib/libgnutls.so.26.4.5
b7684000-b7689000 r--p 00097000 08:01 270496     /usr/lib/libgnutls.so.26.4.5
b7689000-b768a000 rw-p 0009c000 08:01 270496     /usr/lib/libgnutls.so.26.4.5
b768a000-b76a0000 r-xp 00000000 08:01 270844     /usr/lib/libsasl2.so.2.0.22
b76a0000-b76a1000 r--p 00015000 08:01 270844     /usr/lib/libsasl2.so.2.0.22
b76a1000-b76a2000 rw-p 00016000 08:01 270844     /usr/lib/libsasl2.so.2.0.22
b76a2000-b76ae000 r-xp 00000000 08:01 270630     /usr/lib/liblber-2.4.so.2.1.0
b76ae000-b76af000 r--p 0000b000 08:01 270630     /usr/lib/liblber-2.4.so.2.1.0
b76af000-b76b0000 rw-p 0000c000 08:01 270630     /usr/lib/liblber-2.4.so.2.1.0
b76b0000-b76b7000 r-xp 00000000 08:01 164666     /lib/tls/i686/cmov/librt-2.8.90.so
b76b7000-b76b8000 r--p 00007000 08:01 164666     /lib/tls/i686/cmov/librt-2.8.90.so
b76b8000-b76b9000 rw-p 00008000 08:01 164666     /lib/tls/i686/cmov/librt-2.8.90.so
b76b9000-b76f8000 r-xp 00000000 08:01 272393     /usr/lib/libldap_r-2.4.so.2.1.0
b76f8000-b76f9000 r--p 0003e000 08:01 272393     /usr/lib/libldap_r-2.4.so.2.1.0
b76f9000-b76fa000 rw-p 0003f000 08:01 272393     /usr/lib/libldap_r-2.4.so.2.1.0
b76fa000-b76fb000 rw-p b76fa000 00:00 0
b76fb000-b772b000 r-xp 00000000 08:01 271062     /usr/lib/libidn.so.11.5.37
b772b000-b772c000 r--p 00030000 08:01 271062     /usr/lib/libidn.so.11.5.37
b772c000-b772d000 rw-p 00031000 08:01 271062     /usr/lib/libidn.so.11.5.37
b772d000-b7769000 r-xp 00000000 08:01 270492     /usr/lib/libcurl.so.4.1.0
b7769000-b776a000 r--p 0003c000 08:01 270492     /usr/lib/libcurl.so.4.1.0
b776a000-b776b000 rw-p 0003d000 08:01 270492     /usr/lib/libcurl.so.4.1.0
b776b000-b7779000 r-xp 00000000 08:01 311801     /usr/lib/php5/20060613+lfs/curl.so
b7779000-b777a000 rw-p 0000d000 08:01 311801     /usr/lib/php5/20060613+lfs/curl.so

```The test.php looks like this:

```
<?PHP

$optionsCSV = array( 1=>1, 2=>2, 3=>6, 4=>29, 5=>23);

//
$res = TestExtModule_LoadFeedFromLocalCSV(  '/usr/local/www/data-dist/client/stream_escaped.csv', $optionsCSV, true, "\t",  "\"", "\\" );

printf("<?xml version=\"1.0\" encoding=\"UTF-8\"?>\n<items>\n");

while($row = TestExtModule_GetNextFeedNode($res))
{

    printf( "<item><url>%s</url><title><![CDATA[%s]]></title><price><![CDATA[%s]]></price><column1><![CDATA[%s]]></column1><destination_region><![CDATA[%s]]></destination_region></item>\n",
                         str_replace( "&", "&amp;", $row[1] ),
                         html_entity_decode( $row[2], ENT_NOQUOTES, 'UTF-8' ),
                         html_entity_decode( $row[3], ENT_NOQUOTES, 'UTF-8' ),
                         html_entity_decode( $row[4], ENT_NOQUOTES, 'UTF-8' ),
                         filter( $row[5])
                         );
    //}
  unset($row);
}

printf("</items>\n");
print $i.' '.$j;
?>
```Problem #2:
 Maybe you noticed I have an external php module called TestExtModule written in C. In this module a function is invoked, which uses a FILE pointer, and a php_stream pointer somehow like this (I removed several lines to keep it readable):

```

int theFunction( ... )
{
        ...

        php_stream *stream;
        FILE *fp;

        //open streams
        fp = fopen(filename, "rb");
        if (fp)
        {
                stream = php_stream_fopen_from_file(fp, "rb");
                if (!stream)
                {
                        zend_printf("Cannot open file.\n");
                        fclose(fp);
                        return 0;
                }
        }
        else
        {
                zend_printf("Cannot open file.\n");
                return 0;
        }
        while ((buf = php_stream_get_line(stream, NULL, 0, &buf_len)) != NULL)
        {
                ...
        }

        //close the streams
        php_stream_close(stream);
        fclose(fp); // **<= ERROR OCCURS HERE** (I did some debugging)

        return 1;
}

``` The error I get with this code is quite similar to the upper one. It occurs when I run the php file above that invokes LoadFeedFromLocalCSV from the php external module and the theFunction is invoked from there:

```

*** glibc detected *** php: double free or corruption (!prev): 0x098dd6d8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7940454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb79424b6]
/lib/tls/i686/cmov/libc.so.6(fclose+0x144)[0xb7930064]
/usr/lib/php5/20060613+lfs/testextmodule.so(theFunction+0x9f3)[0xb781c133]
/usr/lib/php5/20060613+lfs/testextmodule.so(zif_TestExtModule_LoadFeedFromLocalCSV+0x27f)[0xb781c40f]
php[0x830603f]
php(execute+0x168)[0x82f7308]
php(zend_execute_scripts+0x1c3)[0x82d5a83]
php(php_execute_script+0x1f2)[0x828c1d2]
php(main+0x191d)[0x836b9ad]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb78e7685]
php[0x808f6a1]
======= Memory map: ========
08048000-08589000 r-xp 00000000 08:01 270882     /usr/bin/php5
08589000-085c2000 rw-p 00540000 08:01 270882     /usr/bin/php5
085c2000-085c7000 rw-p 085c2000 00:00 0
09775000-09ea5000 rw-p 09775000 00:00 0          [heap]
b7000000-b7021000 rw-p b7000000 00:00 0
b7021000-b7100000 ---p b7021000 00:00 0
b71a4000-b71b1000 r-xp 00000000 08:01 155856     /lib/libgcc_s.so.1
b71b1000-b71b2000 r--p 0000c000 08:01 155856     /lib/libgcc_s.so.1
b71b2000-b71b3000 rw-p 0000d000 08:01 155856     /lib/libgcc_s.so.1
b71b3000-b7294000 r--p 00000000 08:01 278931     /usr/lib/locale/en_US.utf8/LC_COLLATE
b7294000-b729e000 r-xp 00000000 08:01 164659     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b729e000-b729f000 r--p 00009000 08:01 164659     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b729f000-b72a0000 rw-p 0000a000 08:01 164659     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b72a0000-b72a6000 r-xp 00000000 08:01 311800     /usr/lib/php5/20060613+lfs/pdo_mysql.so
b72a6000-b72a7000 rw-p 00005000 08:01 311800     /usr/lib/php5/20060613+lfs/pdo_mysql.so
b72a7000-b72ba000 r-xp 00000000 08:01 311804     /usr/lib/php5/20060613+lfs/pdo.so
b72ba000-b72bc000 rw-p 00013000 08:01 311804     /usr/lib/php5/20060613+lfs/pdo.so
b72bc000-b72d2000 r-xp 00000000 08:01 311799     /usr/lib/php5/20060613+lfs/mysqli.so
b72d2000-b72d4000 rw-p 00016000 08:01 311799     /usr/lib/php5/20060613+lfs/mysqli.so
b72d4000-b7472000 r-xp 00000000 08:01 272050     /usr/lib/libmysqlclient.so.15.0.0
b7472000-b7473000 ---p 0019e000 08:01 272050     /usr/lib/libmysqlclient.so.15.0.0
b7473000-b7476000 r--p 0019e000 08:01 272050     /usr/lib/libmysqlclient.so.15.0.0
b7476000-b74b6000 rw-p 001a1000 08:01 272050     /usr/lib/libmysqlclient.so.15.0.0
b74b6000-b74b7000 rw-p b74b6000 00:00 0
b74b7000-b74c1000 r-xp 00000000 08:01 311798     /usr/lib/php5/20060613+lfs/mysql.so
b74c1000-b74c2000 rw-p 0000a000 08:01 311798     /usr/lib/php5/20060613+lfs/mysql.so
b74c2000-b74cc000 r-xp 00000000 08:01 155874     /lib/libpam.so.0.81.12
b74cc000-b74cd000 r--p 00009000 08:01 155874     /lib/libpam.so.0.81.12
b74cd000-b74ce000 rw-p 0000a000 08:01 155874     /lib/libpam.so.0.81.12
b74ce000-b75d8000 r-xp 00000000 08:01 462236     /usr/lib/libc-client.so.2007b.0
b75d8000-b75d9000 r--p 0010a000 08:01 462236     /usr/lib/libc-client.so.2007b.0
b75d9000-b75df000 rw-p 0010b000 08:01 462236     /usr/lib/libc-client.so.2007b.0
b75df000-b75e0000 rw-p b75df000 00:00 0
b75e0000-b75f6000 r-xp 00000000 08:01 314818     /usr/lib/php5/20060613+lfs/imap.so
b75f6000-b75f7000 r--p 00015000 08:01 314818     /usr/lib/php5/20060613+lfs/imap.so
b75f7000-b75f8000 rw-p 00016000 08:01 314818     /usr/lib/php5/20060613+lfs/imap.so
b75f8000-b75fb000 r-xp 00000000 08:01 155858     /lib/libgpg-error.so.0.3.0
b75fb000-b75fc000 rw-p 00002000 08:01 155858     /lib/libgpg-error.so.0.3.0
b75fc000-b7662000 r-xp 00000000 08:01 155857     /lib/libgcrypt.so.11.4.4
b7662000-b7663000 r--p 00065000 08:01 155857     /lib/libgcrypt.so.11.4.4
b7663000-b7665000 rw-p 00066000 08:01 155857     /lib/libgcrypt.so.11.4.4
b7665000-b7675000 r-xp 00000000 08:01 271097     /usr/lib/libtasn1.so.3.0.15
b7675000-b7677000 rw-p 0000f000 08:01 271097     /usr/lib/libtasn1.so.3.0.15
b7677000-b770e000 r-xp 00000000 08:01 270496     /usr/lib/libgnutls.so.26.4.5
b770e000-b7713000 r--p 00097000 08:01 270496     /usr/lib/libgnutlAborted

``` I also checked fp, before fclose, and it was not NULL. 

However if I comment out fclose or php_stream_close, everything works fine, but in my opinion I should close both streams...

```

//These works fine without runtime error:
        //php_stream_close(stream);
        fclose(fp);
//OR
        php_stream_close(stream);
         //fclose(fp);

``` I have php5 version 5.2.6 and I also tried 5.2.9 (dotdeb package), these errors occured in both case.

 Any help/suggestion is appreciated. Sorry for the long post, but I really wanted to provide ever neccessary detail to get some help about them. Thanx in advance.

---

### Post by Arndt on 2009-09-03
> **rogerr said:**
> Hi,
 I would like to mention 2 problems here:

Problem #1:

 I have a file called test.php.
 If I run
 everything goes fine.  But if I run 
I get the following huge error:
```

*** glibc detected *** php: double free or corruption (!prev): 0x08e98710 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb78b6454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb78b84b6]
/lib/tls/i686/cmov/libc.so.6(fclose+0x144)[0xb78a6064]
php[0x82a8408]
php(_php_stream_free+0xc7)[0x82a2cb7]
php[0x82a2f18]
php(list_entry_destructor+0xa3)[0x82e3c33]
php[0x82e0904]
php(zend_hash_graceful_reverse_destroy+0x27)[0x82e0bc7]
php(zend_destroy_rsrc_list+0x1d)[0x82e3a7d]
php(zend_deactivate+0xaf)[0x82d5d9f]
php(php_request_shutdown+0x186)[0x828cbe6]
php(main+0x843)[0x836a8d3]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb785d685]
php[0x808f6a1]
======= Memory map: ========
08048000-08589000 r-xp 00000000 08:01 270882     /usr/bin/php5
08589000-085c2000 rw-p 00540000 08:01 270882     /usr/bin/php5
085c2000-085c7000 rw-p 085c2000 00:00 0
08d30000-09460000 rw-p 08d30000 00:00 0          [heap]
b7000000-b7021000 rw-p b7000000 00:00 0
b7021000-b7100000 ---p b7021000 00:00 0
b711a000-b7127000 r-xp 00000000 08:01 155856     /lib/libgcc_s.so.1
b7127000-b7128000 r--p 0000c000 08:01 155856     /lib/libgcc_s.so.1
b7128000-b7129000 rw-p 0000d000 08:01 155856     /lib/libgcc_s.so.1
b7129000-b720a000 r--p 00000000 08:01 278931     /usr/lib/locale/en_US.utf8/LC_COLLATE
b720a000-b7214000 r-xp 00000000 08:01 164659     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7214000-b7215000 r--p 00009000 08:01 164659     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7215000-b7216000 rw-p 0000a000 08:01 164659     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b7216000-b721c000 r-xp 00000000 08:01 311800     /usr/lib/php5/20060613+lfs/pdo_mysql.so
b721c000-b721d000 rw-p 00005000 08:01 311800     /usr/lib/php5/20060613+lfs/pdo_mysql.so
b721d000-b7230000 r-xp 00000000 08:01 311804     /usr/lib/php5/20060613+lfs/pdo.so
b7230000-b7232000 rw-p 00013000 08:01 311804     /usr/lib/php5/20060613+lfs/pdo.so
b7232000-b7248000 r-xp 00000000 08:01 311799     /usr/lib/php5/20060613+lfs/mysqli.so
b7248000-b724a000 rw-p 00016000 08:01 311799     /usr/lib/php5/20060613+lfs/mysqli.so
b724a000-b73e8000 r-xp 00000000 08:01 272050     /usr/lib/libmysqlclient.so.15.0.0
b73e8000-b73e9000 ---p 0019e000 08:01 272050     /usr/lib/libmysqlclient.so.15.0.0
b73e9000-b73ec000 r--p 0019e000 08:01 272050     /usr/lib/libmysqlclient.so.15.0.0
b73ec000-b742c000 rw-p 001a1000 08:01 272050     /usr/lib/libmysqlclient.so.15.0.0
b742c000-b742d000 rw-p b742c000 00:00 0
b742d000-b7437000 r-xp 00000000 08:01 311798     /usr/lib/php5/20060613+lfs/mysql.so
b7437000-b7438000 rw-p 0000a000 08:01 311798     /usr/lib/php5/20060613+lfs/mysql.so
b7438000-b7442000 r-xp 00000000 08:01 155874     /lib/libpam.so.0.81.12
b7442000-b7443000 r--p 00009000 08:01 155874     /lib/libpam.so.0.81.12
b7443000-b7444000 rw-p 0000a000 08:01 155874     /lib/libpam.so.0.81.12
b7444000-b754e000 r-xp 00000000 08:01 462236     /usr/lib/libc-client.so.2007b.0
b754e000-b754f000 r--p 0010a000 08:01 462236     /usr/lib/libc-client.so.2007b.0
b754f000-b7555000 rw-p 0010b000 08:01 462236     /usr/lib/libc-client.so.2007b.0
b7555000-b7556000 rw-p b7555000 00:00 0
b7556000-b756c000 r-xp 00000000 08:01 314818     /usr/lib/php5/20060613+lfs/imap.so
b756c000-b756d000 r--p 00015000 08:01 314818     /usr/lib/php5/20060613+lfs/imap.so
b756d000-b756e000 rw-p 00016000 08:01 314818     /usr/lib/php5/20060613+lfs/imap.so
b756e000-b7571000 r-xp 00000000 08:01 155858     /lib/libgpg-error.so.0.3.0
b7571000-b7572000 rw-p 00002000 08:01 155858     /lib/libgpg-error.so.0.3.0
b7572000-b75d8000 r-xp 00000000 08:01 155857     /lib/libgcrypt.so.11.4.4
b75d8000-b75d9000 r--p 00065000 08:01 155857     /lib/libgcrypt.so.11.4.4
b75d9000-b75db000 rw-p 00066000 08:01 155857     /lib/libgcrypt.so.11.4.4
b75db000-b75eb000 r-xp 00000000 08:01 271097     /usr/lib/libtasn1.so.3.0.15
b75eb000-b75ed000 rw-p 0000f000 08:01 271097     /usr/lib/libtasn1.so.3.0.15
b75ed000-b7684000 r-xp 00000000 08:01 270496     /usr/lib/libgnutls.so.26.4.5
b7684000-b7689000 r--p 00097000 08:01 270496     /usr/lib/libgnutls.so.26.4.5
b7689000-b768a000 rw-p 0009c000 08:01 270496     /usr/lib/libgnutls.so.26.4.5
b768a000-b76a0000 r-xp 00000000 08:01 270844     /usr/lib/libsasl2.so.2.0.22
b76a0000-b76a1000 r--p 00015000 08:01 270844     /usr/lib/libsasl2.so.2.0.22
b76a1000-b76a2000 rw-p 00016000 08:01 270844     /usr/lib/libsasl2.so.2.0.22
b76a2000-b76ae000 r-xp 00000000 08:01 270630     /usr/lib/liblber-2.4.so.2.1.0
b76ae000-b76af000 r--p 0000b000 08:01 270630     /usr/lib/liblber-2.4.so.2.1.0
b76af000-b76b0000 rw-p 0000c000 08:01 270630     /usr/lib/liblber-2.4.so.2.1.0
b76b0000-b76b7000 r-xp 00000000 08:01 164666     /lib/tls/i686/cmov/librt-2.8.90.so
b76b7000-b76b8000 r--p 00007000 08:01 164666     /lib/tls/i686/cmov/librt-2.8.90.so
b76b8000-b76b9000 rw-p 00008000 08:01 164666     /lib/tls/i686/cmov/librt-2.8.90.so
b76b9000-b76f8000 r-xp 00000000 08:01 272393     /usr/lib/libldap_r-2.4.so.2.1.0
b76f8000-b76f9000 r--p 0003e000 08:01 272393     /usr/lib/libldap_r-2.4.so.2.1.0
b76f9000-b76fa000 rw-p 0003f000 08:01 272393     /usr/lib/libldap_r-2.4.so.2.1.0
b76fa000-b76fb000 rw-p b76fa000 00:00 0
b76fb000-b772b000 r-xp 00000000 08:01 271062     /usr/lib/libidn.so.11.5.37
b772b000-b772c000 r--p 00030000 08:01 271062     /usr/lib/libidn.so.11.5.37
b772c000-b772d000 rw-p 00031000 08:01 271062     /usr/lib/libidn.so.11.5.37
b772d000-b7769000 r-xp 00000000 08:01 270492     /usr/lib/libcurl.so.4.1.0
b7769000-b776a000 r--p 0003c000 08:01 270492     /usr/lib/libcurl.so.4.1.0
b776a000-b776b000 rw-p 0003d000 08:01 270492     /usr/lib/libcurl.so.4.1.0
b776b000-b7779000 r-xp 00000000 08:01 311801     /usr/lib/php5/20060613+lfs/curl.so
b7779000-b777a000 rw-p 0000d000 08:01 311801     /usr/lib/php5/20060613+lfs/curl.so

```The test.php looks like this:

```
<?PHP

$optionsCSV = array( 1=>1, 2=>2, 3=>6, 4=>29, 5=>23);

//
$res = TestExtModule_LoadFeedFromLocalCSV(  '/usr/local/www/data-dist/client/stream_escaped.csv', $optionsCSV, true, "\t",  "\"", "\\" );

printf("<?xml version=\"1.0\" encoding=\"UTF-8\"?>\n<items>\n");

while($row = TestExtModule_GetNextFeedNode($res))
{

    printf( "<item><url>%s</url><title><![CDATA[%s]]></title><price><![CDATA[%s]]></price><column1><![CDATA[%s]]></column1><destination_region><![CDATA[%s]]></destination_region></item>\n",
                         str_replace( "&", "&amp;", $row[1] ),
                         html_entity_decode( $row[2], ENT_NOQUOTES, 'UTF-8' ),
                         html_entity_decode( $row[3], ENT_NOQUOTES, 'UTF-8' ),
                         html_entity_decode( $row[4], ENT_NOQUOTES, 'UTF-8' ),
                         filter( $row[5])
                         );
    //}
  unset($row);
}

printf("</items>\n");
print $i.' '.$j;
?>
```Problem #2:
 Maybe you noticed I have an external php module called TestExtModule written in C. In this module a function is invoked, which uses a FILE pointer, and a php_stream pointer somehow like this (I removed several lines to keep it readable):

```

int theFunction( ... )
{
        ...

        php_stream *stream;
        FILE *fp;

        //open streams
        fp = fopen(filename, "rb");
        if (fp)
        {
                stream = php_stream_fopen_from_file(fp, "rb");
                if (!stream)
                {
                        zend_printf("Cannot open file.\n");
                        fclose(fp);
                        return 0;
                }
        }
        else
        {
                zend_printf("Cannot open file.\n");
                return 0;
        }
        while ((buf = php_stream_get_line(stream, NULL, 0, &buf_len)) != NULL)
        {
                ...
        }

        //close the streams
        php_stream_close(stream);
        fclose(fp); // **<= ERROR OCCURS HERE** (I did some debugging)

        return 1;
}

``` The error I get with this code is quite similar to the upper one. It occurs when I run the php file above that invokes LoadFeedFromLocalCSV from the php external module and the theFunction is invoked from there:

```

*** glibc detected *** php: double free or corruption (!prev): 0x098dd6d8 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7940454]
/lib/tls/i686/cmov/libc.so.6(cfree+0x96)[0xb79424b6]
/lib/tls/i686/cmov/libc.so.6(fclose+0x144)[0xb7930064]
/usr/lib/php5/20060613+lfs/testextmodule.so(theFunction+0x9f3)[0xb781c133]
/usr/lib/php5/20060613+lfs/testextmodule.so(zif_TestExtModule_LoadFeedFromLocalCSV+0x27f)[0xb781c40f]
php[0x830603f]
php(execute+0x168)[0x82f7308]
php(zend_execute_scripts+0x1c3)[0x82d5a83]
php(php_execute_script+0x1f2)[0x828c1d2]
php(main+0x191d)[0x836b9ad]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5)[0xb78e7685]
php[0x808f6a1]
======= Memory map: ========
08048000-08589000 r-xp 00000000 08:01 270882     /usr/bin/php5
08589000-085c2000 rw-p 00540000 08:01 270882     /usr/bin/php5
085c2000-085c7000 rw-p 085c2000 00:00 0
09775000-09ea5000 rw-p 09775000 00:00 0          [heap]
b7000000-b7021000 rw-p b7000000 00:00 0
b7021000-b7100000 ---p b7021000 00:00 0
b71a4000-b71b1000 r-xp 00000000 08:01 155856     /lib/libgcc_s.so.1
b71b1000-b71b2000 r--p 0000c000 08:01 155856     /lib/libgcc_s.so.1
b71b2000-b71b3000 rw-p 0000d000 08:01 155856     /lib/libgcc_s.so.1
b71b3000-b7294000 r--p 00000000 08:01 278931     /usr/lib/locale/en_US.utf8/LC_COLLATE
b7294000-b729e000 r-xp 00000000 08:01 164659     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b729e000-b729f000 r--p 00009000 08:01 164659     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b729f000-b72a0000 rw-p 0000a000 08:01 164659     /lib/tls/i686/cmov/libnss_files-2.8.90.so
b72a0000-b72a6000 r-xp 00000000 08:01 311800     /usr/lib/php5/20060613+lfs/pdo_mysql.so
b72a6000-b72a7000 rw-p 00005000 08:01 311800     /usr/lib/php5/20060613+lfs/pdo_mysql.so
b72a7000-b72ba000 r-xp 00000000 08:01 311804     /usr/lib/php5/20060613+lfs/pdo.so
b72ba000-b72bc000 rw-p 00013000 08:01 311804     /usr/lib/php5/20060613+lfs/pdo.so
b72bc000-b72d2000 r-xp 00000000 08:01 311799     /usr/lib/php5/20060613+lfs/mysqli.so
b72d2000-b72d4000 rw-p 00016000 08:01 311799     /usr/lib/php5/20060613+lfs/mysqli.so
b72d4000-b7472000 r-xp 00000000 08:01 272050     /usr/lib/libmysqlclient.so.15.0.0
b7472000-b7473000 ---p 0019e000 08:01 272050     /usr/lib/libmysqlclient.so.15.0.0
b7473000-b7476000 r--p 0019e000 08:01 272050     /usr/lib/libmysqlclient.so.15.0.0
b7476000-b74b6000 rw-p 001a1000 08:01 272050     /usr/lib/libmysqlclient.so.15.0.0
b74b6000-b74b7000 rw-p b74b6000 00:00 0
b74b7000-b74c1000 r-xp 00000000 08:01 311798     /usr/lib/php5/20060613+lfs/mysql.so
b74c1000-b74c2000 rw-p 0000a000 08:01 311798     /usr/lib/php5/20060613+lfs/mysql.so
b74c2000-b74cc000 r-xp 00000000 08:01 155874     /lib/libpam.so.0.81.12
b74cc000-b74cd000 r--p 00009000 08:01 155874     /lib/libpam.so.0.81.12
b74cd000-b74ce000 rw-p 0000a000 08:01 155874     /lib/libpam.so.0.81.12
b74ce000-b75d8000 r-xp 00000000 08:01 462236     /usr/lib/libc-client.so.2007b.0
b75d8000-b75d9000 r--p 0010a000 08:01 462236     /usr/lib/libc-client.so.2007b.0
b75d9000-b75df000 rw-p 0010b000 08:01 462236     /usr/lib/libc-client.so.2007b.0
b75df000-b75e0000 rw-p b75df000 00:00 0
b75e0000-b75f6000 r-xp 00000000 08:01 314818     /usr/lib/php5/20060613+lfs/imap.so
b75f6000-b75f7000 r--p 00015000 08:01 314818     /usr/lib/php5/20060613+lfs/imap.so
b75f7000-b75f8000 rw-p 00016000 08:01 314818     /usr/lib/php5/20060613+lfs/imap.so
b75f8000-b75fb000 r-xp 00000000 08:01 155858     /lib/libgpg-error.so.0.3.0
b75fb000-b75fc000 rw-p 00002000 08:01 155858     /lib/libgpg-error.so.0.3.0
b75fc000-b7662000 r-xp 00000000 08:01 155857     /lib/libgcrypt.so.11.4.4
b7662000-b7663000 r--p 00065000 08:01 155857     /lib/libgcrypt.so.11.4.4
b7663000-b7665000 rw-p 00066000 08:01 155857     /lib/libgcrypt.so.11.4.4
b7665000-b7675000 r-xp 00000000 08:01 271097     /usr/lib/libtasn1.so.3.0.15
b7675000-b7677000 rw-p 0000f000 08:01 271097     /usr/lib/libtasn1.so.3.0.15
b7677000-b770e000 r-xp 00000000 08:01 270496     /usr/lib/libgnutls.so.26.4.5
b770e000-b7713000 r--p 00097000 08:01 270496     /usr/lib/libgnutlAborted

``` I also checked fp, before fclose, and it was not NULL. 

However if I comment out fclose or php_stream_close, everything works fine, but in my opinion I should close both streams...

```

//These works fine without runtime error:
        //php_stream_close(stream);
        fclose(fp);
//OR
        php_stream_close(stream);
         //fclose(fp);

``` I have php5 version 5.2.6 and I also tried 5.2.9 (dotdeb package), these errors occured in both case.

 Any help/suggestion is appreciated. Sorry for the long post, but I really wanted to provide ever neccessary detail to get some help about them. Thanx in advance.

Googling for php_stream_close brings up pages with this text:

>  php_stream_close() safely closes stream  and releases the resources associated with it. After stream  has been closed, it's value is undefined and should not be used.

php_stream_close() returns 0 if the stream was closed or EOF to indicate an error. Regardless of the success of the call, stream is undefined and should not be used after a call to this function.

---

