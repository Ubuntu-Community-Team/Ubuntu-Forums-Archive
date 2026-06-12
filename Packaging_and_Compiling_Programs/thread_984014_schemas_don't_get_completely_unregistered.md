---
title: "schemas don't get completely unregistered"
date: 2008-11-16
forum: Packaging and Compiling Programs
---

### Post by frafu on 2008-11-16
Hello, 

I am trying to add a schemas file to the onboard python package. On installation, the schemas file gets installed into /usr/share/gconf/schemas and the dh_gconf call in debian/rules adds the gconf-schemas --register and gconf-schemas --unregister calls to the postinst and prerm scripts. 

Here is the debian/rules file: 
```
 
#!/usr/bin/make -f

include /usr/share/cdbs/1/rules/debhelper.mk

DEB_PYTHON_SYSTEM               := pycentral
include /usr/share/cdbs/1/class/python-distutils.mk

binary-install/onboard::
	dh_gconf

``` 

Here is the schemas file: 
```
 
<?xml version="1.0"?>
<gconfschemafile>
    <schemalist>
      <schema>
        <key>/schemas/apps/onboard/layout_filename</key>
        <applyto>/apps/onboard/layout_filename</applyto>
        <owner>onboard</owner>
        <type>string</type>
        <default>Default</default>
        <locale name="C">
          <short>Layout filename</short>
          <long>Name of the file with the current layout.</long>
        </locale>
      </schema>
      <schema>
        <key>/schemas/apps/onboard/scanning_interval</key>
        <applyto>/apps/onboard/scanning_interval</applyto>
        <owner>onboard</owner>
        <type>int</type>
        <default>750</default>
        <locale name="C">
          <short>Scanning Interval</short>
          <long>Length of the pause between two steps in scanning mode.</long>
        </locale>
      </schema>
      <schema>
        <key>/schemas/apps/onboard/sizeX</key>
        <applyto>/apps/onboard/sizeX</applyto>
        <owner>onboard</owner>
        <type>int</type>
        <default>800</default>
        <locale name="C">
          <short>Horizontal size</short>
          <long>Horizontal size of the onboard keyboard area.</long>
        </locale>
      </schema>
      <schema>
        <key>/schemas/apps/onboard/sizeY</key>
        <applyto>/apps/onboard/sizeY</applyto>
        <owner>onboard</owner>
        <type>int</type>
        <default>300</default>
        <locale name="C">
          <short>Vertical size</short>
          <long>Vertical size of the onboard keyboard area.</long>
        </locale>
      </schema>
    </schemalist>
</gconfschemafile>

``` 

And now to the problem: 
After completely uninstalling the package and the implicit unregistration of the keys, I have the following in the gconf database when I check it with the gconf editor: 
- the keys in /apps/onboard are not available anymore, but 
- the /apps/onboard entry is still listed, even after restarting the computer. 

Could anybody please tell me how to get rid of the /apps/onboard entry? 

Thanks in advance for any help. 

Cheers 

Francesco

---

