---
title: "[SOLVED] sudo rm -r doesnt acutally remove anything"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by dynamethod on 2008-06-04
**EDIT Answer to this problem is here: [http://ubuntuforums.org/showpost.php?p=5110529&postcount=11](http://ubuntuforums.org/showpost.php?p=5110529&postcount=11)**

Hey im trying to uninstall apache2 so i ran ```
sudo apt-get remove --purge apache2
```

but when i run ```
whereis apache2
``` it shows:

```
apache2: /usr/sbin/apache2 /usr/lib/apache2 /usr/share/apache2 /usr/share/man/man8/apache2.8.gz
```


and also when i run: ```
locate apache2
```  it shows:

```
/etc/apache2
/etc/bash_completion.d/apache2.2-common
/etc/cron.daily/apache2
/etc/default/apache2
/etc/init.d/apache2
/etc/logrotate.d/apache2
/etc/php5/apache2
/etc/php5/apache2/conf.d
/etc/php5/apache2/php.ini
/etc/rc0.d/K09apache2
/etc/rc1.d/K09apache2
/etc/rc3.d/S91apache2
/etc/rc4.d/S91apache2
/etc/rc5.d/S91apache2
/etc/rc6.d/K09apache2
/usr/lib/apache2
/usr/lib/apache2/modules
/usr/lib/apache2/suexec
/usr/lib/apache2/modules/httpd.exp
/usr/lib/apache2/modules/libphp5.so
/usr/lib/apache2/modules/mod_actions.so
/usr/lib/apache2/modules/mod_alias.so
/usr/lib/apache2/modules/mod_asis.so
/usr/lib/apache2/modules/mod_auth_basic.so
/usr/lib/apache2/modules/mod_auth_digest.so
/usr/lib/apache2/modules/mod_authn_alias.so
/usr/lib/apache2/modules/mod_authn_anon.so
/usr/lib/apache2/modules/mod_authn_dbd.so
/usr/lib/apache2/modules/mod_authn_dbm.so
/usr/lib/apache2/modules/mod_authn_default.so
/usr/lib/apache2/modules/mod_authn_file.so
/usr/lib/apache2/modules/mod_authnz_ldap.so
/usr/lib/apache2/modules/mod_authz_dbm.so
/usr/lib/apache2/modules/mod_authz_default.so
/usr/lib/apache2/modules/mod_authz_groupfile.so
/usr/lib/apache2/modules/mod_authz_host.so
/usr/lib/apache2/modules/mod_authz_owner.so
/usr/lib/apache2/modules/mod_authz_user.so
/usr/lib/apache2/modules/mod_autoindex.so
/usr/lib/apache2/modules/mod_cache.so
/usr/lib/apache2/modules/mod_cern_meta.so
/usr/lib/apache2/modules/mod_cgi.so
/usr/lib/apache2/modules/mod_cgid.so
/usr/lib/apache2/modules/mod_charset_lite.so
/usr/lib/apache2/modules/mod_dav.so
/usr/lib/apache2/modules/mod_dav_fs.so
/usr/lib/apache2/modules/mod_dav_lock.so
/usr/lib/apache2/modules/mod_dbd.so
/usr/lib/apache2/modules/mod_deflate.so
/usr/lib/apache2/modules/mod_dir.so
/usr/lib/apache2/modules/mod_disk_cache.so
/usr/lib/apache2/modules/mod_dumpio.so
/usr/lib/apache2/modules/mod_env.so
/usr/lib/apache2/modules/mod_expires.so
/usr/lib/apache2/modules/mod_ext_filter.so
/usr/lib/apache2/modules/mod_file_cache.so
/usr/lib/apache2/modules/mod_filter.so
/usr/lib/apache2/modules/mod_headers.so
/usr/lib/apache2/modules/mod_ident.so
/usr/lib/apache2/modules/mod_imagemap.so
/usr/lib/apache2/modules/mod_include.so
/usr/lib/apache2/modules/mod_info.so
/usr/lib/apache2/modules/mod_ldap.so
/usr/lib/apache2/modules/mod_log_forensic.so
/usr/lib/apache2/modules/mod_mem_cache.so
/usr/lib/apache2/modules/mod_mime.so
/usr/lib/apache2/modules/mod_mime_magic.so
/usr/lib/apache2/modules/mod_negotiation.so
/usr/lib/apache2/modules/mod_proxy.so
/usr/lib/apache2/modules/mod_proxy_ajp.so
/usr/lib/apache2/modules/mod_proxy_balancer.so
/usr/lib/apache2/modules/mod_proxy_connect.so
/usr/lib/apache2/modules/mod_proxy_ftp.so
/usr/lib/apache2/modules/mod_proxy_http.so
/usr/lib/apache2/modules/mod_rewrite.so
/usr/lib/apache2/modules/mod_setenvif.so
/usr/lib/apache2/modules/mod_speling.so
/usr/lib/apache2/modules/mod_ssl.so
/usr/lib/apache2/modules/mod_status.so
/usr/lib/apache2/modules/mod_substitute.so
/usr/lib/apache2/modules/mod_suexec.so
/usr/lib/apache2/modules/mod_unique_id.so
/usr/lib/apache2/modules/mod_userdir.so
/usr/lib/apache2/modules/mod_usertrack.so
/usr/lib/apache2/modules/mod_version.so
/usr/lib/apache2/modules/mod_vhost_alias.so
/usr/sbin/apache2
/usr/sbin/apache2ctl
/usr/share/apache2
/usr/share/apache2/build
/usr/share/apache2/default-site
/usr/share/apache2/error
/usr/share/apache2/icons
/usr/share/apache2/build/envvars-std
/usr/share/apache2/default-site/index.html
/usr/share/apache2/error/HTTP_BAD_GATEWAY.html.var
/usr/share/apache2/error/HTTP_BAD_REQUEST.html.var
/usr/share/apache2/error/HTTP_FORBIDDEN.html.var
/usr/share/apache2/error/HTTP_GONE.html.var
/usr/share/apache2/error/HTTP_INTERNAL_SERVER_ERROR.html.var
/usr/share/apache2/error/HTTP_LENGTH_REQUIRED.html.var
/usr/share/apache2/error/HTTP_METHOD_NOT_ALLOWED.html.var
/usr/share/apache2/error/HTTP_NOT_FOUND.html.var
/usr/share/apache2/error/HTTP_NOT_IMPLEMENTED.html.var
/usr/share/apache2/error/HTTP_PRECONDITION_FAILED.html.var
/usr/share/apache2/error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
/usr/share/apache2/error/HTTP_REQUEST_TIME_OUT.html.var
/usr/share/apache2/error/HTTP_REQUEST_URI_TOO_LARGE.html.var
/usr/share/apache2/error/HTTP_SERVICE_UNAVAILABLE.html.var
/usr/share/apache2/error/HTTP_UNAUTHORIZED.html.var
/usr/share/apache2/error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
/usr/share/apache2/error/HTTP_VARIANT_ALSO_VARIES.html.var
/usr/share/apache2/error/README
/usr/share/apache2/error/contact.html.var
/usr/share/apache2/error/include
/usr/share/apache2/error/include/bottom.html
/usr/share/apache2/error/include/spacer.html
/usr/share/apache2/error/include/top.html
/usr/share/apache2/icons/README
/usr/share/apache2/icons/README.html
/usr/share/apache2/icons/a.gif
/usr/share/apache2/icons/a.png
/usr/share/apache2/icons/alert.black.gif
/usr/share/apache2/icons/alert.black.png
/usr/share/apache2/icons/alert.red.gif
/usr/share/apache2/icons/alert.red.png
/usr/share/apache2/icons/apache_pb.gif
/usr/share/apache2/icons/apache_pb.png
/usr/share/apache2/icons/apache_pb2.gif
/usr/share/apache2/icons/apache_pb2.png
/usr/share/apache2/icons/apache_pb2_ani.gif
/usr/share/apache2/icons/back.gif
/usr/share/apache2/icons/back.png
/usr/share/apache2/icons/ball.gray.gif
/usr/share/apache2/icons/ball.gray.png
/usr/share/apache2/icons/ball.red.gif
/usr/share/apache2/icons/ball.red.png
/usr/share/apache2/icons/binary.gif
/usr/share/apache2/icons/binary.png
/usr/share/apache2/icons/binhex.gif
/usr/share/apache2/icons/binhex.png
/usr/share/apache2/icons/blank.gif
/usr/share/apache2/icons/blank.png
/usr/share/apache2/icons/bomb.gif
/usr/share/apache2/icons/bomb.png
/usr/share/apache2/icons/box1.gif
/usr/share/apache2/icons/box1.png
/usr/share/apache2/icons/box2.gif
/usr/share/apache2/icons/box2.png
/usr/share/apache2/icons/broken.gif
/usr/share/apache2/icons/broken.png
/usr/share/apache2/icons/burst.gif
/usr/share/apache2/icons/burst.png
/usr/share/apache2/icons/c.gif
/usr/share/apache2/icons/c.png
/usr/share/apache2/icons/comp.blue.gif
/usr/share/apache2/icons/comp.blue.png
/usr/share/apache2/icons/comp.gray.gif
/usr/share/apache2/icons/comp.gray.png
/usr/share/apache2/icons/compressed.gif
/usr/share/apache2/icons/compressed.png
/usr/share/apache2/icons/continued.gif
/usr/share/apache2/icons/continued.png
/usr/share/apache2/icons/dir.gif
/usr/share/apache2/icons/dir.png
/usr/share/apache2/icons/diskimg.gif
/usr/share/apache2/icons/diskimg.png
/usr/share/apache2/icons/down.gif
/usr/share/apache2/icons/down.png
/usr/share/apache2/icons/dvi.gif
/usr/share/apache2/icons/dvi.png
/usr/share/apache2/icons/f.gif
/usr/share/apache2/icons/f.png
/usr/share/apache2/icons/folder.gif
/usr/share/apache2/icons/folder.open.gif
/usr/share/apache2/icons/folder.open.png
/usr/share/apache2/icons/folder.png
/usr/share/apache2/icons/folder.sec.gif
/usr/share/apache2/icons/folder.sec.png
/usr/share/apache2/icons/forward.gif
/usr/share/apache2/icons/forward.png
/usr/share/apache2/icons/generic.gif
/usr/share/apache2/icons/generic.png
/usr/share/apache2/icons/generic.red.gif
/usr/share/apache2/icons/generic.red.png
/usr/share/apache2/icons/generic.sec.gif
/usr/share/apache2/icons/generic.sec.png
/usr/share/apache2/icons/hand.right.gif
/usr/share/apache2/icons/hand.right.png
/usr/share/apache2/icons/hand.up.gif
/usr/share/apache2/icons/hand.up.png
/usr/share/apache2/icons/icon.sheet.gif
/usr/share/apache2/icons/icon.sheet.png
/usr/share/apache2/icons/image1.gif
/usr/share/apache2/icons/image1.png
/usr/share/apache2/icons/image2.gif
/usr/share/apache2/icons/image2.png
/usr/share/apache2/icons/image3.gif
/usr/share/apache2/icons/image3.png
/usr/share/apache2/icons/index.gif
/usr/share/apache2/icons/index.png
/usr/share/apache2/icons/layout.gif
/usr/share/apache2/icons/layout.png
/usr/share/apache2/icons/left.gif
/usr/share/apache2/icons/left.png
/usr/share/apache2/icons/link.gif
/usr/share/apache2/icons/link.png
/usr/share/apache2/icons/movie.gif
/usr/share/apache2/icons/movie.png
/usr/share/apache2/icons/odf6odb-20x22.png
/usr/share/apache2/icons/odf6odc-20x22.png
/usr/share/apache2/icons/odf6odf-20x22.png
/usr/share/apache2/icons/odf6odg-20x22.png
/usr/share/apache2/icons/odf6odi-20x22.png
/usr/share/apache2/icons/odf6odm-20x22.png
/usr/share/apache2/icons/odf6odp-20x22.png
/usr/share/apache2/icons/odf6ods-20x22.png
/usr/share/apache2/icons/odf6odt-20x22.png
/usr/share/apache2/icons/odf6otc-20x22.png
/usr/share/apache2/icons/odf6otf-20x22.png
/usr/share/apache2/icons/odf6otg-20x22.png
/usr/share/apache2/icons/odf6oth-20x22.png
/usr/share/apache2/icons/odf6oti-20x22.png
/usr/share/apache2/icons/odf6otp-20x22.png
/usr/share/apache2/icons/odf6ots-20x22.png
/usr/share/apache2/icons/odf6ott-20x22.png
/usr/share/apache2/icons/p.gif
/usr/share/apache2/icons/p.png
/usr/share/apache2/icons/patch.gif
/usr/share/apache2/icons/patch.png
/usr/share/apache2/icons/pdf.gif
/usr/share/apache2/icons/pdf.png
/usr/share/apache2/icons/pie0.gif
/usr/share/apache2/icons/pie0.png
/usr/share/apache2/icons/pie1.gif
/usr/share/apache2/icons/pie1.png
/usr/share/apache2/icons/pie2.gif
/usr/share/apache2/icons/pie2.png
/usr/share/apache2/icons/pie3.gif
/usr/share/apache2/icons/pie3.png
/usr/share/apache2/icons/pie4.gif
/usr/share/apache2/icons/pie4.png
/usr/share/apache2/icons/pie5.gif
/usr/share/apache2/icons/pie5.png
/usr/share/apache2/icons/pie6.gif
/usr/share/apache2/icons/pie6.png
/usr/share/apache2/icons/pie7.gif
/usr/share/apache2/icons/pie7.png
/usr/share/apache2/icons/pie8.gif
/usr/share/apache2/icons/pie8.png
/usr/share/apache2/icons/portal.gif
/usr/share/apache2/icons/portal.png
/usr/share/apache2/icons/ps.gif
/usr/share/apache2/icons/ps.png
/usr/share/apache2/icons/quill.gif
/usr/share/apache2/icons/quill.png
/usr/share/apache2/icons/right.gif
/usr/share/apache2/icons/right.png
/usr/share/apache2/icons/screw1.gif
/usr/share/apache2/icons/screw1.png
/usr/share/apache2/icons/screw2.gif
/usr/share/apache2/icons/screw2.png
/usr/share/apache2/icons/script.gif
/usr/share/apache2/icons/script.png
/usr/share/apache2/icons/small
/usr/share/apache2/icons/sound1.gif
/usr/share/apache2/icons/sound1.png
/usr/share/apache2/icons/sound2.gif
/usr/share/apache2/icons/sound2.png
/usr/share/apache2/icons/sphere1.gif
/usr/share/apache2/icons/sphere1.png
/usr/share/apache2/icons/sphere2.gif
/usr/share/apache2/icons/sphere2.png
/usr/share/apache2/icons/tar.gif
/usr/share/apache2/icons/tar.png
/usr/share/apache2/icons/tex.gif
/usr/share/apache2/icons/tex.png
/usr/share/apache2/icons/text.gif
/usr/share/apache2/icons/text.png
/usr/share/apache2/icons/transfer.gif
/usr/share/apache2/icons/transfer.png
/usr/share/apache2/icons/unknown.gif
/usr/share/apache2/icons/unknown.png
/usr/share/apache2/icons/up.gif
/usr/share/apache2/icons/up.png
/usr/share/apache2/icons/uu.gif
/usr/share/apache2/icons/uu.png
/usr/share/apache2/icons/uuencoded.gif
/usr/share/apache2/icons/uuencoded.png
/usr/share/apache2/icons/world1.gif
/usr/share/apache2/icons/world1.png
/usr/share/apache2/icons/world2.gif
/usr/share/apache2/icons/world2.png
/usr/share/apache2/icons/small/back.gif
/usr/share/apache2/icons/small/back.png
/usr/share/apache2/icons/small/binary.gif
/usr/share/apache2/icons/small/binary.png
/usr/share/apache2/icons/small/binhex.gif
/usr/share/apache2/icons/small/binhex.png
/usr/share/apache2/icons/small/blank.gif
/usr/share/apache2/icons/small/blank.png
/usr/share/apache2/icons/small/broken.gif
/usr/share/apache2/icons/small/broken.png
/usr/share/apache2/icons/small/burst.gif
/usr/share/apache2/icons/small/burst.png
/usr/share/apache2/icons/small/comp1.gif
/usr/share/apache2/icons/small/comp1.png
/usr/share/apache2/icons/small/comp2.gif
/usr/share/apache2/icons/small/comp2.png
/usr/share/apache2/icons/small/compressed.gif
/usr/share/apache2/icons/small/compressed.png
/usr/share/apache2/icons/small/continued.gif
/usr/share/apache2/icons/small/continued.png
/usr/share/apache2/icons/small/dir.gif
/usr/share/apache2/icons/small/dir.png
/usr/share/apache2/icons/small/dir2.gif
/usr/share/apache2/icons/small/dir2.png
/usr/share/apache2/icons/small/doc.gif
/usr/share/apache2/icons/small/doc.png
/usr/share/apache2/icons/small/forward.gif
/usr/share/apache2/icons/small/forward.png
/usr/share/apache2/icons/small/generic.gif
/usr/share/apache2/icons/small/generic.png
/usr/share/apache2/icons/small/generic2.gif
/usr/share/apache2/icons/small/generic2.png
/usr/share/apache2/icons/small/generic3.gif
/usr/share/apache2/icons/small/generic3.png
/usr/share/apache2/icons/small/image.gif
/usr/share/apache2/icons/small/image.png
/usr/share/apache2/icons/small/image2.gif
/usr/share/apache2/icons/small/image2.png
/usr/share/apache2/icons/small/index.gif
/usr/share/apache2/icons/small/index.png
/usr/share/apache2/icons/small/key.gif
/usr/share/apache2/icons/small/key.png
/usr/share/apache2/icons/small/movie.gif
/usr/share/apache2/icons/small/movie.png
/usr/share/apache2/icons/small/patch.gif
/usr/share/apache2/icons/small/patch.png
/usr/share/apache2/icons/small/ps.gif
/usr/share/apache2/icons/small/ps.png
/usr/share/apache2/icons/small/rainbow.gif
/usr/share/apache2/icons/small/rainbow.png
/usr/share/apache2/icons/small/sound.gif
/usr/share/apache2/icons/small/sound.png
/usr/share/apache2/icons/small/sound2.gif
/usr/share/apache2/icons/small/sound2.png
/usr/share/apache2/icons/small/tar.gif
/usr/share/apache2/icons/small/tar.png
/usr/share/apache2/icons/small/text.gif
/usr/share/apache2/icons/small/text.png
/usr/share/apache2/icons/small/transfer.gif
/usr/share/apache2/icons/small/transfer.png
/usr/share/apache2/icons/small/unknown.gif
/usr/share/apache2/icons/small/unknown.png
/usr/share/apache2/icons/small/uu.gif
/usr/share/apache2/icons/small/uu.png
/usr/share/bug/apache2
/usr/share/bug/apache2-mpm-prefork
/usr/share/bug/apache2.2-common
/usr/share/bug/apache2-mpm-prefork/script
/usr/share/bug/apache2.2-common/control
/usr/share/bug/apache2.2-common/script
/usr/share/doc/apache2
/usr/share/doc/apache2-mpm-prefork
/usr/share/doc/apache2-utils
/usr/share/doc/apache2.2-common
/usr/share/doc/libapache2-mod-php5
/usr/share/doc/apache2-mpm-prefork/NEWS.Debian.gz
/usr/share/doc/apache2-mpm-prefork/changelog.Debian.gz
/usr/share/doc/apache2-mpm-prefork/changelog.gz
/usr/share/doc/apache2-mpm-prefork/copyright
/usr/share/doc/apache2-utils/changelog.Debian.gz
/usr/share/doc/apache2-utils/changelog.gz
/usr/share/doc/apache2-utils/copyright
/usr/share/doc/apache2.2-common/NEWS.Debian.gz
/usr/share/doc/apache2.2-common/README.Debian.gz
/usr/share/doc/apache2.2-common/README.backtrace
/usr/share/doc/apache2.2-common/changelog.Debian.gz
/usr/share/doc/apache2.2-common/changelog.gz
/usr/share/doc/apache2.2-common/copyright
/usr/share/doc/apache2.2-common/examples
/usr/share/doc/apache2.2-common/examples/apache2
/usr/share/doc/apache2.2-common/examples/apache2/apache2.conf.gz
/usr/share/doc/apache2.2-common/examples/apache2/extra
/usr/share/doc/apache2.2-common/examples/apache2/magic.gz
/usr/share/doc/apache2.2-common/examples/apache2/mime.types.gz
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-autoindex.conf
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-dav.conf
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-default.conf
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-info.conf
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-languages.conf.gz
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-manual.conf
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-mpm.conf
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-multilang-errordoc.conf
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-ssl.conf.gz
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-userdir.conf
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-vhosts.conf
/usr/share/doc/librpc-xml-perl/README.apache2
/usr/share/lintian/overrides/apache2-mpm-prefork
/usr/share/lintian/overrides/apache2.2-common
/usr/share/man/man8/apache2.8.gz
/usr/share/man/man8/apache2ctl.8.gz
/var/cache/apache2
/var/cache/apache2/mod_disk_cache
/var/cache/apache2/reload
/var/cache/apt/archives/apache2-mpm-prefork_2.2.8-1ubuntu0.1_i386.deb
/var/cache/apt/archives/apache2-utils_2.2.8-1ubuntu0.1_i386.deb
/var/cache/apt/archives/apache2.2-common_2.2.8-1ubuntu0.1_i386.deb
/var/cache/apt/archives/apache2_2.2.8-1ubuntu0.1_all.deb
/var/cache/apt/archives/libapache2-mod-php5_5.2.4-2ubuntu5.1_i386.deb
/var/lib/dpkg/info/apache2-mpm-prefork.list
/var/lib/dpkg/info/apache2-mpm-prefork.md5sums
/var/lib/dpkg/info/apache2-mpm-prefork.postinst
/var/lib/dpkg/info/apache2-mpm-prefork.preinst
/var/lib/dpkg/info/apache2-mpm-prefork.prerm
/var/lib/dpkg/info/apache2-utils.list
/var/lib/dpkg/info/apache2-utils.md5sums
/var/lib/dpkg/info/apache2.2-common.conffiles
/var/lib/dpkg/info/apache2.2-common.list
/var/lib/dpkg/info/apache2.2-common.md5sums
/var/lib/dpkg/info/apache2.2-common.postinst
/var/lib/dpkg/info/apache2.2-common.postrm
/var/lib/dpkg/info/apache2.2-common.preinst
/var/lib/dpkg/info/apache2.list
/var/lib/dpkg/info/apache2.md5sums
/var/lib/dpkg/info/libapache2-mod-php5.conffiles
/var/lib/dpkg/info/libapache2-mod-php5.list
/var/lib/dpkg/info/libapache2-mod-php5.md5sums
/var/lib/dpkg/info/libapache2-mod-php5.postinst
/var/lib/dpkg/info/libapache2-mod-php5.postrm
/var/lib/dpkg/info/libapache2-mod-php5.prerm
/var/log/apache2
/var/log/apache2/access.log
/var/log/apache2/access.log.1
/var/log/apache2/access.log.2.gz
/var/log/apache2/access.log.3.gz
/var/log/apache2/access.log.4.gz
/var/log/apache2/access.log.5.gz
/var/log/apache2/error.log
/var/log/apache2/error.log.1
/var/log/apache2/error.log.2.gz
/var/log/apache2/error.log.3.gz
/var/log/apache2/error.log.4.gz
/var/log/apache2/error.log.5.gz

```

so, how do i actually remove it all?

---

### Post by starcannon on 2008-06-04
rm -r is for a recursive removal

Lets say you have a folder located at:

/home/myhome/junk

and lets say that junk contains absolutely nothing we want to keep

rm -r /home/myhome/junk

that command will delete the folder named "junk" and everything inside of it.

Be very careful with recursive rm, if you point at the wrong folder by mistake.... ouch.

For more information on rm
```
man rm
```

---

### Post by dynamethod on 2008-06-04
so i do ```
sudo apt-get remove -r apache2
``` instead?

edit, that dont work, i dont really want to have to go through each of those dir's individually to delete them, why werent they removed when i removed apache2?

---

### Post by starcannon on 2008-06-04
rm is not the same thing as apt-get

I think the command you want for apt-get is remove

so:
```
sudo apt-get remove packageNameHere
```
or for more thorough cleaning out of program
```
sudo apt-get --purge packageNameHere
```

Keep in mind almost everything has a man page:

```
man apt-get
```

---

### Post by dynamethod on 2008-06-04
Yeah im well aware of the sudo apt-get remove thing, but the problem is that its not actually removing anything, as shown here:

[http://paste.ubuntu.com/16757/](http://paste.ubuntu.com/16757/)

---

### Post by Maestro23 on 2008-06-04
> sudo apt-get --purge remove packagename 

Removes a installed package (configfiles will also be removed)

AptGet HowTo: [https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto](https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto)

---

### Post by dynamethod on 2008-06-04
lol, thanks guys but im quiet adept to apt-get etc, the problem is that its not removing anything here:

[http://paste.ubuntu.com/16757/](http://paste.ubuntu.com/16757/)

---

### Post by dynamethod on 2008-06-04
```
sudo apt-get install apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  apache2
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B/44.3kB of archives.
After this operation, 102kB of additional disk space will be used.
Selecting previously deselected package apache2.
(Reading database ... 140648 files and directories currently installed.)
Unpacking apache2 (from .../apache2_2.2.8-1ubuntu0.1_all.deb) ...
Setting up apache2 (2.2.8-1ubuntu0.1) ...
xen@darksun:~$ sudo apt-get --purge remove apache2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  apache2*
0 upgraded, 0 newly installed, 1 to remove and 10 not upgraded.
After this operation, 102kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140654 files and directories currently installed.)
Removing apache2 ...
xen@darksun:~$ locate apache2
/etc/bash_completion.d/apache2.2-common
/etc/cron.daily/apache2
/etc/default/apache2
/etc/init.d/apache2
/etc/logrotate.d/apache2
/etc/php5/apache2
/etc/php5/apache2/conf.d
/etc/php5/apache2/php.ini
/etc/rc0.d/K09apache2
/etc/rc1.d/K09apache2
/etc/rc3.d/S91apache2
/etc/rc4.d/S91apache2
/etc/rc5.d/S91apache2
/etc/rc6.d/K09apache2
/usr/lib/apache2
/usr/lib/apache2/modules
/usr/lib/apache2/suexec
/usr/lib/apache2/modules/httpd.exp
/usr/lib/apache2/modules/libphp5.so
/usr/lib/apache2/modules/mod_actions.so
/usr/lib/apache2/modules/mod_alias.so
/usr/lib/apache2/modules/mod_asis.so
/usr/lib/apache2/modules/mod_auth_basic.so
/usr/lib/apache2/modules/mod_auth_digest.so
/usr/lib/apache2/modules/mod_authn_alias.so
/usr/lib/apache2/modules/mod_authn_anon.so
/usr/lib/apache2/modules/mod_authn_dbd.so
/usr/lib/apache2/modules/mod_authn_dbm.so
/usr/lib/apache2/modules/mod_authn_default.so
/usr/lib/apache2/modules/mod_authn_file.so
/usr/lib/apache2/modules/mod_authnz_ldap.so
/usr/lib/apache2/modules/mod_authz_dbm.so
/usr/lib/apache2/modules/mod_authz_default.so
/usr/lib/apache2/modules/mod_authz_groupfile.so
/usr/lib/apache2/modules/mod_authz_host.so
/usr/lib/apache2/modules/mod_authz_owner.so
/usr/lib/apache2/modules/mod_authz_user.so
/usr/lib/apache2/modules/mod_autoindex.so
/usr/lib/apache2/modules/mod_cache.so
/usr/lib/apache2/modules/mod_cern_meta.so
/usr/lib/apache2/modules/mod_cgi.so
/usr/lib/apache2/modules/mod_cgid.so
/usr/lib/apache2/modules/mod_charset_lite.so
/usr/lib/apache2/modules/mod_dav.so
/usr/lib/apache2/modules/mod_dav_fs.so
/usr/lib/apache2/modules/mod_dav_lock.so
/usr/lib/apache2/modules/mod_dbd.so
/usr/lib/apache2/modules/mod_deflate.so
/usr/lib/apache2/modules/mod_dir.so
/usr/lib/apache2/modules/mod_disk_cache.so
/usr/lib/apache2/modules/mod_dumpio.so
/usr/lib/apache2/modules/mod_env.so
/usr/lib/apache2/modules/mod_expires.so
/usr/lib/apache2/modules/mod_ext_filter.so
/usr/lib/apache2/modules/mod_file_cache.so
/usr/lib/apache2/modules/mod_filter.so
/usr/lib/apache2/modules/mod_headers.so
/usr/lib/apache2/modules/mod_ident.so
/usr/lib/apache2/modules/mod_imagemap.so
/usr/lib/apache2/modules/mod_include.so
/usr/lib/apache2/modules/mod_info.so
/usr/lib/apache2/modules/mod_ldap.so
/usr/lib/apache2/modules/mod_log_forensic.so
/usr/lib/apache2/modules/mod_mem_cache.so
/usr/lib/apache2/modules/mod_mime.so
/usr/lib/apache2/modules/mod_mime_magic.so
/usr/lib/apache2/modules/mod_negotiation.so
/usr/lib/apache2/modules/mod_proxy.so
/usr/lib/apache2/modules/mod_proxy_ajp.so
/usr/lib/apache2/modules/mod_proxy_balancer.so
/usr/lib/apache2/modules/mod_proxy_connect.so
/usr/lib/apache2/modules/mod_proxy_ftp.so
/usr/lib/apache2/modules/mod_proxy_http.so
/usr/lib/apache2/modules/mod_rewrite.so
/usr/lib/apache2/modules/mod_setenvif.so
/usr/lib/apache2/modules/mod_speling.so
/usr/lib/apache2/modules/mod_ssl.so
/usr/lib/apache2/modules/mod_status.so
/usr/lib/apache2/modules/mod_substitute.so
/usr/lib/apache2/modules/mod_suexec.so
/usr/lib/apache2/modules/mod_unique_id.so
/usr/lib/apache2/modules/mod_userdir.so
/usr/lib/apache2/modules/mod_usertrack.so
/usr/lib/apache2/modules/mod_version.so
/usr/lib/apache2/modules/mod_vhost_alias.so
/usr/sbin/apache2
/usr/sbin/apache2ctl
/usr/share/apache2
/usr/share/apache2/build
/usr/share/apache2/default-site
/usr/share/apache2/error
/usr/share/apache2/icons
/usr/share/apache2/build/envvars-std
/usr/share/apache2/default-site/index.html
/usr/share/apache2/error/HTTP_BAD_GATEWAY.html.var
/usr/share/apache2/error/HTTP_BAD_REQUEST.html.var
/usr/share/apache2/error/HTTP_FORBIDDEN.html.var
/usr/share/apache2/error/HTTP_GONE.html.var
/usr/share/apache2/error/HTTP_INTERNAL_SERVER_ERROR.html.var
/usr/share/apache2/error/HTTP_LENGTH_REQUIRED.html.var
/usr/share/apache2/error/HTTP_METHOD_NOT_ALLOWED.html.var
/usr/share/apache2/error/HTTP_NOT_FOUND.html.var
/usr/share/apache2/error/HTTP_NOT_IMPLEMENTED.html.var
/usr/share/apache2/error/HTTP_PRECONDITION_FAILED.html.var
/usr/share/apache2/error/HTTP_REQUEST_ENTITY_TOO_LARGE.html.var
/usr/share/apache2/error/HTTP_REQUEST_TIME_OUT.html.var
/usr/share/apache2/error/HTTP_REQUEST_URI_TOO_LARGE.html.var
/usr/share/apache2/error/HTTP_SERVICE_UNAVAILABLE.html.var
/usr/share/apache2/error/HTTP_UNAUTHORIZED.html.var
/usr/share/apache2/error/HTTP_UNSUPPORTED_MEDIA_TYPE.html.var
/usr/share/apache2/error/HTTP_VARIANT_ALSO_VARIES.html.var
/usr/share/apache2/error/README
/usr/share/apache2/error/contact.html.var
/usr/share/apache2/error/include
/usr/share/apache2/error/include/bottom.html
/usr/share/apache2/error/include/spacer.html
/usr/share/apache2/error/include/top.html
/usr/share/apache2/icons/README
/usr/share/apache2/icons/README.html
/usr/share/apache2/icons/a.gif
/usr/share/apache2/icons/a.png
/usr/share/apache2/icons/alert.black.gif
/usr/share/apache2/icons/alert.black.png
/usr/share/apache2/icons/alert.red.gif
/usr/share/apache2/icons/alert.red.png
/usr/share/apache2/icons/apache_pb.gif
/usr/share/apache2/icons/apache_pb.png
/usr/share/apache2/icons/apache_pb2.gif
/usr/share/apache2/icons/apache_pb2.png
/usr/share/apache2/icons/apache_pb2_ani.gif
/usr/share/apache2/icons/back.gif
/usr/share/apache2/icons/back.png
/usr/share/apache2/icons/ball.gray.gif
/usr/share/apache2/icons/ball.gray.png
/usr/share/apache2/icons/ball.red.gif
/usr/share/apache2/icons/ball.red.png
/usr/share/apache2/icons/binary.gif
/usr/share/apache2/icons/binary.png
/usr/share/apache2/icons/binhex.gif
/usr/share/apache2/icons/binhex.png
/usr/share/apache2/icons/blank.gif
/usr/share/apache2/icons/blank.png
/usr/share/apache2/icons/bomb.gif
/usr/share/apache2/icons/bomb.png
/usr/share/apache2/icons/box1.gif
/usr/share/apache2/icons/box1.png
/usr/share/apache2/icons/box2.gif
/usr/share/apache2/icons/box2.png
/usr/share/apache2/icons/broken.gif
/usr/share/apache2/icons/broken.png
/usr/share/apache2/icons/burst.gif
/usr/share/apache2/icons/burst.png
/usr/share/apache2/icons/c.gif
/usr/share/apache2/icons/c.png
/usr/share/apache2/icons/comp.blue.gif
/usr/share/apache2/icons/comp.blue.png
/usr/share/apache2/icons/comp.gray.gif
/usr/share/apache2/icons/comp.gray.png
/usr/share/apache2/icons/compressed.gif
/usr/share/apache2/icons/compressed.png
/usr/share/apache2/icons/continued.gif
/usr/share/apache2/icons/continued.png
/usr/share/apache2/icons/dir.gif
/usr/share/apache2/icons/dir.png
/usr/share/apache2/icons/diskimg.gif
/usr/share/apache2/icons/diskimg.png
/usr/share/apache2/icons/down.gif
/usr/share/apache2/icons/down.png
/usr/share/apache2/icons/dvi.gif
/usr/share/apache2/icons/dvi.png
/usr/share/apache2/icons/f.gif
/usr/share/apache2/icons/f.png
/usr/share/apache2/icons/folder.gif
/usr/share/apache2/icons/folder.open.gif
/usr/share/apache2/icons/folder.open.png
/usr/share/apache2/icons/folder.png
/usr/share/apache2/icons/folder.sec.gif
/usr/share/apache2/icons/folder.sec.png
/usr/share/apache2/icons/forward.gif
/usr/share/apache2/icons/forward.png
/usr/share/apache2/icons/generic.gif
/usr/share/apache2/icons/generic.png
/usr/share/apache2/icons/generic.red.gif
/usr/share/apache2/icons/generic.red.png
/usr/share/apache2/icons/generic.sec.gif
/usr/share/apache2/icons/generic.sec.png
/usr/share/apache2/icons/hand.right.gif
/usr/share/apache2/icons/hand.right.png
/usr/share/apache2/icons/hand.up.gif
/usr/share/apache2/icons/hand.up.png
/usr/share/apache2/icons/icon.sheet.gif
/usr/share/apache2/icons/icon.sheet.png
/usr/share/apache2/icons/image1.gif
/usr/share/apache2/icons/image1.png
/usr/share/apache2/icons/image2.gif
/usr/share/apache2/icons/image2.png
/usr/share/apache2/icons/image3.gif
/usr/share/apache2/icons/image3.png
/usr/share/apache2/icons/index.gif
/usr/share/apache2/icons/index.png
/usr/share/apache2/icons/layout.gif
/usr/share/apache2/icons/layout.png
/usr/share/apache2/icons/left.gif
/usr/share/apache2/icons/left.png
/usr/share/apache2/icons/link.gif
/usr/share/apache2/icons/link.png
/usr/share/apache2/icons/movie.gif
/usr/share/apache2/icons/movie.png
/usr/share/apache2/icons/odf6odb-20x22.png
/usr/share/apache2/icons/odf6odc-20x22.png
/usr/share/apache2/icons/odf6odf-20x22.png
/usr/share/apache2/icons/odf6odg-20x22.png
/usr/share/apache2/icons/odf6odi-20x22.png
/usr/share/apache2/icons/odf6odm-20x22.png
/usr/share/apache2/icons/odf6odp-20x22.png
/usr/share/apache2/icons/odf6ods-20x22.png
/usr/share/apache2/icons/odf6odt-20x22.png
/usr/share/apache2/icons/odf6otc-20x22.png
/usr/share/apache2/icons/odf6otf-20x22.png
/usr/share/apache2/icons/odf6otg-20x22.png
/usr/share/apache2/icons/odf6oth-20x22.png
/usr/share/apache2/icons/odf6oti-20x22.png
/usr/share/apache2/icons/odf6otp-20x22.png
/usr/share/apache2/icons/odf6ots-20x22.png
/usr/share/apache2/icons/odf6ott-20x22.png
/usr/share/apache2/icons/p.gif
/usr/share/apache2/icons/p.png
/usr/share/apache2/icons/patch.gif
/usr/share/apache2/icons/patch.png
/usr/share/apache2/icons/pdf.gif
/usr/share/apache2/icons/pdf.png
/usr/share/apache2/icons/pie0.gif
/usr/share/apache2/icons/pie0.png
/usr/share/apache2/icons/pie1.gif
/usr/share/apache2/icons/pie1.png
/usr/share/apache2/icons/pie2.gif
/usr/share/apache2/icons/pie2.png
/usr/share/apache2/icons/pie3.gif
/usr/share/apache2/icons/pie3.png
/usr/share/apache2/icons/pie4.gif
/usr/share/apache2/icons/pie4.png
/usr/share/apache2/icons/pie5.gif
/usr/share/apache2/icons/pie5.png
/usr/share/apache2/icons/pie6.gif
/usr/share/apache2/icons/pie6.png
/usr/share/apache2/icons/pie7.gif
/usr/share/apache2/icons/pie7.png
/usr/share/apache2/icons/pie8.gif
/usr/share/apache2/icons/pie8.png
/usr/share/apache2/icons/portal.gif
/usr/share/apache2/icons/portal.png
/usr/share/apache2/icons/ps.gif
/usr/share/apache2/icons/ps.png
/usr/share/apache2/icons/quill.gif
/usr/share/apache2/icons/quill.png
/usr/share/apache2/icons/right.gif
/usr/share/apache2/icons/right.png
/usr/share/apache2/icons/screw1.gif
/usr/share/apache2/icons/screw1.png
/usr/share/apache2/icons/screw2.gif
/usr/share/apache2/icons/screw2.png
/usr/share/apache2/icons/script.gif
/usr/share/apache2/icons/script.png
/usr/share/apache2/icons/small
/usr/share/apache2/icons/sound1.gif
/usr/share/apache2/icons/sound1.png
/usr/share/apache2/icons/sound2.gif
/usr/share/apache2/icons/sound2.png
/usr/share/apache2/icons/sphere1.gif
/usr/share/apache2/icons/sphere1.png
/usr/share/apache2/icons/sphere2.gif
/usr/share/apache2/icons/sphere2.png
/usr/share/apache2/icons/tar.gif
/usr/share/apache2/icons/tar.png
/usr/share/apache2/icons/tex.gif
/usr/share/apache2/icons/tex.png
/usr/share/apache2/icons/text.gif
/usr/share/apache2/icons/text.png
/usr/share/apache2/icons/transfer.gif
/usr/share/apache2/icons/transfer.png
/usr/share/apache2/icons/unknown.gif
/usr/share/apache2/icons/unknown.png
/usr/share/apache2/icons/up.gif
/usr/share/apache2/icons/up.png
/usr/share/apache2/icons/uu.gif
/usr/share/apache2/icons/uu.png
/usr/share/apache2/icons/uuencoded.gif
/usr/share/apache2/icons/uuencoded.png
/usr/share/apache2/icons/world1.gif
/usr/share/apache2/icons/world1.png
/usr/share/apache2/icons/world2.gif
/usr/share/apache2/icons/world2.png
/usr/share/apache2/icons/small/back.gif
/usr/share/apache2/icons/small/back.png
/usr/share/apache2/icons/small/binary.gif
/usr/share/apache2/icons/small/binary.png
/usr/share/apache2/icons/small/binhex.gif
/usr/share/apache2/icons/small/binhex.png
/usr/share/apache2/icons/small/blank.gif
/usr/share/apache2/icons/small/blank.png
/usr/share/apache2/icons/small/broken.gif
/usr/share/apache2/icons/small/broken.png
/usr/share/apache2/icons/small/burst.gif
/usr/share/apache2/icons/small/burst.png
/usr/share/apache2/icons/small/comp1.gif
/usr/share/apache2/icons/small/comp1.png
/usr/share/apache2/icons/small/comp2.gif
/usr/share/apache2/icons/small/comp2.png
/usr/share/apache2/icons/small/compressed.gif
/usr/share/apache2/icons/small/compressed.png
/usr/share/apache2/icons/small/continued.gif
/usr/share/apache2/icons/small/continued.png
/usr/share/apache2/icons/small/dir.gif
/usr/share/apache2/icons/small/dir.png
/usr/share/apache2/icons/small/dir2.gif
/usr/share/apache2/icons/small/dir2.png
/usr/share/apache2/icons/small/doc.gif
/usr/share/apache2/icons/small/doc.png
/usr/share/apache2/icons/small/forward.gif
/usr/share/apache2/icons/small/forward.png
/usr/share/apache2/icons/small/generic.gif
/usr/share/apache2/icons/small/generic.png
/usr/share/apache2/icons/small/generic2.gif
/usr/share/apache2/icons/small/generic2.png
/usr/share/apache2/icons/small/generic3.gif
/usr/share/apache2/icons/small/generic3.png
/usr/share/apache2/icons/small/image.gif
/usr/share/apache2/icons/small/image.png
/usr/share/apache2/icons/small/image2.gif
/usr/share/apache2/icons/small/image2.png
/usr/share/apache2/icons/small/index.gif
/usr/share/apache2/icons/small/index.png
/usr/share/apache2/icons/small/key.gif
/usr/share/apache2/icons/small/key.png
/usr/share/apache2/icons/small/movie.gif
/usr/share/apache2/icons/small/movie.png
/usr/share/apache2/icons/small/patch.gif
/usr/share/apache2/icons/small/patch.png
/usr/share/apache2/icons/small/ps.gif
/usr/share/apache2/icons/small/ps.png
/usr/share/apache2/icons/small/rainbow.gif
/usr/share/apache2/icons/small/rainbow.png
/usr/share/apache2/icons/small/sound.gif
/usr/share/apache2/icons/small/sound.png
/usr/share/apache2/icons/small/sound2.gif
/usr/share/apache2/icons/small/sound2.png
/usr/share/apache2/icons/small/tar.gif
/usr/share/apache2/icons/small/tar.png
/usr/share/apache2/icons/small/text.gif
/usr/share/apache2/icons/small/text.png
/usr/share/apache2/icons/small/transfer.gif
/usr/share/apache2/icons/small/transfer.png
/usr/share/apache2/icons/small/unknown.gif
/usr/share/apache2/icons/small/unknown.png
/usr/share/apache2/icons/small/uu.gif
/usr/share/apache2/icons/small/uu.png
/usr/share/bug/apache2-mpm-prefork
/usr/share/bug/apache2.2-common
/usr/share/bug/apache2-mpm-prefork/script
/usr/share/bug/apache2.2-common/control
/usr/share/bug/apache2.2-common/script
/usr/share/doc/apache2-mpm-prefork
/usr/share/doc/apache2-utils
/usr/share/doc/apache2.2-common
/usr/share/doc/libapache2-mod-php5
/usr/share/doc/apache2-mpm-prefork/NEWS.Debian.gz
/usr/share/doc/apache2-mpm-prefork/changelog.Debian.gz
/usr/share/doc/apache2-mpm-prefork/changelog.gz
/usr/share/doc/apache2-mpm-prefork/copyright
/usr/share/doc/apache2-utils/changelog.Debian.gz
/usr/share/doc/apache2-utils/changelog.gz
/usr/share/doc/apache2-utils/copyright
/usr/share/doc/apache2.2-common/NEWS.Debian.gz
/usr/share/doc/apache2.2-common/README.Debian.gz
/usr/share/doc/apache2.2-common/README.backtrace
/usr/share/doc/apache2.2-common/changelog.Debian.gz
/usr/share/doc/apache2.2-common/changelog.gz
/usr/share/doc/apache2.2-common/copyright
/usr/share/doc/apache2.2-common/examples
/usr/share/doc/apache2.2-common/examples/apache2
/usr/share/doc/apache2.2-common/examples/apache2/apache2.conf.gz
/usr/share/doc/apache2.2-common/examples/apache2/extra
/usr/share/doc/apache2.2-common/examples/apache2/magic.gz
/usr/share/doc/apache2.2-common/examples/apache2/mime.types.gz
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-autoindex.conf
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-dav.conf
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-default.conf
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-info.conf
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-languages.conf.gz
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-manual.conf
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-mpm.conf
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-multilang-errordoc.conf
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-ssl.conf.gz
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-userdir.conf
/usr/share/doc/apache2.2-common/examples/apache2/extra/httpd-vhosts.conf
/usr/share/doc/librpc-xml-perl/README.apache2
/usr/share/lintian/overrides/apache2-mpm-prefork
/usr/share/lintian/overrides/apache2.2-common
/usr/share/man/man8/apache2.8.gz
/usr/share/man/man8/apache2ctl.8.gz
/var/cache/apache2
/var/cache/apache2/mod_disk_cache
/var/cache/apache2/reload
/var/cache/apt/archives/apache2-mpm-prefork_2.2.8-1ubuntu0.1_i386.deb
/var/cache/apt/archives/apache2-utils_2.2.8-1ubuntu0.1_i386.deb
/var/cache/apt/archives/apache2.2-common_2.2.8-1ubuntu0.1_i386.deb
/var/cache/apt/archives/apache2_2.2.8-1ubuntu0.1_all.deb
/var/cache/apt/archives/libapache2-mod-php5_5.2.4-2ubuntu5.1_i386.deb
/var/lib/dpkg/info/apache2-mpm-prefork.list
/var/lib/dpkg/info/apache2-mpm-prefork.md5sums
/var/lib/dpkg/info/apache2-mpm-prefork.postinst
/var/lib/dpkg/info/apache2-mpm-prefork.preinst
/var/lib/dpkg/info/apache2-mpm-prefork.prerm
/var/lib/dpkg/info/apache2-utils.list
/var/lib/dpkg/info/apache2-utils.md5sums
/var/lib/dpkg/info/apache2.2-common.conffiles
/var/lib/dpkg/info/apache2.2-common.list
/var/lib/dpkg/info/apache2.2-common.md5sums
/var/lib/dpkg/info/apache2.2-common.postinst
/var/lib/dpkg/info/apache2.2-common.postrm
/var/lib/dpkg/info/apache2.2-common.preinst
/var/lib/dpkg/info/libapache2-mod-php5.conffiles
/var/lib/dpkg/info/libapache2-mod-php5.list
/var/lib/dpkg/info/libapache2-mod-php5.md5sums
/var/lib/dpkg/info/libapache2-mod-php5.postinst
/var/lib/dpkg/info/libapache2-mod-php5.postrm
/var/lib/dpkg/info/libapache2-mod-php5.prerm
/var/log/apache2
/var/log/apache2/access.log
/var/log/apache2/access.log.1
/var/log/apache2/access.log.2.gz
/var/log/apache2/access.log.3.gz
/var/log/apache2/access.log.4.gz
/var/log/apache2/access.log.5.gz
/var/log/apache2/error.log
/var/log/apache2/error.log.1
/var/log/apache2/error.log.2.gz
/var/log/apache2/error.log.3.gz
/var/log/apache2/error.log.4.gz
/var/log/apache2/error.log.5.gz

```

sigh

---

### Post by jediborger on 2008-06-04
First of all does apt-get give you any errors as to why the package isn't being removed? It's possible something got messed up and apt-get will refuse to remove the package, so try the following:
```
sudo apt-get update
```
This will bring your repositories up to date.
```
sudo apt-get check
```
This should verify your packages and dependencies, if there's an issue this command should resolve it or tell you what's wrong and we can work from there. 

Your command is fine, but your title is wrong which seems to be causing some confusion.

---

### Post by spiderbatdad on 2008-06-04
```
sudo updatedb
locate apache2
```

---

### Post by dynamethod on 2008-06-04
Acutally (and thanks to nickrud on the irc forums) the "package" apache2 is acutally a 'metapackage', i was given this command to run:

```
dpkg  -l '*apache*' | grep ^ii
```

which lists the packages contained with in the 'metapackage'

which after showed up this:

```
ii  apache2-mpm-prefork                        2.2.8-1ubuntu0.1                                   Traditional model for Apache HTTPD
ii  apache2-utils                              2.2.8-1ubuntu0.1                                   utility programs for webservers
ii  apache2.2-common                           2.2.8-1ubuntu0.1                                   Next generation, scalable, extendable web se
ii  libapache2-mod-php5                        5.2.4-2ubuntu5.1                                   server-side, HTML-embedded scripting languag

```

this is how nickrud explained the command ```
dpkg  -l '*apache*' | grep ^ii
```

```
<nickrud> xen_ dpkg -l lists all packages that match *apache* , and the grep ^ii finds all that are installed (that's what the ii means)
```

pretty bloody handy actually!

so i just then had to run: 

```
sudo apt-get --purge remove apache2-mpm-prefork apache2-utils apache2.2-common libapache2-mod-php5
```

---

### Post by starcannon on 2008-06-04
ack nm I'm an idiot hehe, happy you found a solution.

---

