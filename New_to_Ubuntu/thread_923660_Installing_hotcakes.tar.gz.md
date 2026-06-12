---
title: "Installing hotcakes.tar.gz"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by abennett on 2008-09-18
Ok, heres the deal.. I have been reading for hours and hours now about how to unzip a tar.gz file and then ./configure it...make it... make install... IT SIMPLY DOES NOT WORK FOR ME.Forum after forum. Ive tried everything. I've updated my system. Something about the gcc.. thats installed. Keep in mind I've only used Ubuntu for a week. How in the world do I install this program????
Thanks

---

### Post by MegaJim on 2008-09-18
What are you trying to install?  Do you have a link to the site where you got it/a readme file?

---

### Post by nowshining on 2008-09-18
we need a copy of the error message??

have u looked in the repos for a copy of it? a deb on another site? an rpm - if u find an rpm it's easy to convert to a deb and install...

---

### Post by okey666 on 2008-09-18
ok... As you've found out some apps are not compiled to run immediately on linux. To do this you must compile them yourself.
 First check
```
sudo apt-get install build-essential
```
Then unzip your program in some convenient location and run, though the terminal(in the directory):
```
./configure
```

Then, if no errors are made, type:
```
make
```

And if still no errors:
```
make install
```

It may also help if you tell us what on earth this program is. You could also attach it so we could have ago.

edit:If you get any errors post them here.

---

### Post by Therion on 2008-09-18
Hotcakes.tar.gz ... Are you serious?  

Have you checked to see if you have the *flapjacks-generic* dev kit installed?  

Maybe there are some unmet syrup dependencies???

```
flip install
```

---

### Post by abennett on 2008-09-18
As stated in the title, Im installing hotcakes. I have done the build essentials and ./configure..make...make install 90 billion times. Does not work. 
Here is the URL to the website of the program that I am trying to install.

---

### Post by Tatty on 2008-09-18
It would help it you copied and pasted all your terminal output so we can see where it is going wrong.

---

### Post by abennett on 2008-09-18
Yes, Im serious. I have no idea what flapjacks-generic dev kit is. Remember I have only been using this for a week.. Please be nice and take baby steps

---

### Post by Therion on 2008-09-18
> **abennett said:**
> Yes, Im serious. I have no idea what flapjacks-generic dev kit is. Remember I have only been using this for a week.. Please be nice and take baby steps
Sorry, i was joking around with you.  Ignore my previous post.

---

### Post by nowshining on 2008-09-18
try

it was a joke :/

---

### Post by abennett on 2008-09-18
This is what I get when I run tar -zxvf again for the 9th time.



tar: hotcakes/webroot/doc/hotcakes_cookbook/x51.html: Cannot open: File exists
hotcakes/webroot/doc/hotcakes_cookbook/x258.html
tar: hotcakes/webroot/doc/hotcakes_cookbook/x258.html: Cannot open: File exists
hotcakes/webroot/doc/hotcakes_cookbook/x771.html
tar: hotcakes/webroot/doc/hotcakes_cookbook/x771.html: Cannot open: File exists
hotcakes/webroot/doc/hotcakes_cookbook/openwrt.odg
tar: hotcakes/webroot/doc/hotcakes_cookbook/openwrt.odg: Cannot open: File exists
hotcakes/webroot/doc/hotcakes_cookbook/images/
hotcakes/webroot/doc/hotcakes_cookbook/images/openwrt.png
tar: hotcakes/webroot/doc/hotcakes_cookbook/images/openwrt.png: Cannot open: File exists
hotcakes/webroot/doc/hotcakes_cookbook/images/nas_devices.png
tar: hotcakes/webroot/doc/hotcakes_cookbook/images/nas_devices.png: Cannot open: File exists
hotcakes/webroot/doc/hotcakes_cookbook/images/1.png
tar: hotcakes/webroot/doc/hotcakes_cookbook/images/1.png: Cannot open: File exists
hotcakes/webroot/doc/images/
tar: hotcakes/webroot/doc/hotcakes_cookbook/images: Cannot utime: Operation not permitted
tar: hotcakes/webroot/doc/hotcakes_cookbook: Cannot utime: Operation not permitted
hotcakes/webroot/doc/images/tip.gif
tar: hotcakes/webroot/doc/images/tip.gif: Cannot open: File exists
hotcakes/webroot/doc/images/warning.gif
tar: hotcakes/webroot/doc/images/warning.gif: Cannot open: File exists
hotcakes/webroot/doc/images/note.gif
tar: hotcakes/webroot/doc/images/note.gif: Cannot open: File exists
hotcakes/webroot/favicon.ico
tar: hotcakes/webroot/doc/images: Cannot utime: Operation not permitted
tar: hotcakes/webroot/doc: Cannot utime: Operation not permitted
tar: hotcakes/webroot/favicon.ico: Cannot open: File exists
hotcakes/webroot/generated/
hotcakes/webroot/img/
tar: hotcakes/webroot/generated: Cannot utime: Operation not permitted
hotcakes/webroot/img/acro.png
tar: hotcakes/webroot/img/acro.png: Cannot open: File exists
hotcakes/webroot/img/w3c_xhtml10.png
tar: hotcakes/webroot/img/w3c_xhtml10.png: Cannot open: File exists
hotcakes/webroot/img/menu/
hotcakes/webroot/img/menu/edit_user.png
tar: hotcakes/webroot/img/menu/edit_user.png: Cannot open: File exists
hotcakes/webroot/img/menu/help.png
tar: hotcakes/webroot/img/menu/help.png: Cannot open: File exists
hotcakes/webroot/img/menu/logout.png
tar: hotcakes/webroot/img/menu/logout.png: Cannot open: File exists
hotcakes/webroot/img/menu/documentation.png
tar: hotcakes/webroot/img/menu/documentation.png: Cannot open: File exists
hotcakes/webroot/img/menu/document.png
tar: hotcakes/webroot/img/menu/document.png: Cannot open: File exists
hotcakes/webroot/img/menu/user_permanent.png
tar: hotcakes/webroot/img/menu/user_permanent.png: Cannot open: File exists
hotcakes/webroot/img/menu/hotcakes.png
tar: hotcakes/webroot/img/menu/hotcakes.png: Cannot open: File exists
hotcakes/webroot/img/mail.png
tar: hotcakes/webroot/img/menu: Cannot utime: Operation not permitted
tar: hotcakes/webroot/img/mail.png: Cannot open: File exists
hotcakes/webroot/img/nas_generic.gif
tar: hotcakes/webroot/img/nas_generic.gif: Cannot open: File exists
hotcakes/webroot/img/d.gif
tar: hotcakes/webroot/img/d.gif: Cannot open: File exists
hotcakes/webroot/img/cake.power.png
tar: hotcakes/webroot/img/cake.power.png: Cannot open: File exists
hotcakes/webroot/img/next.gif
tar: hotcakes/webroot/img/next.gif: Cannot open: File exists
hotcakes/webroot/img/w3c_css.png
tar: hotcakes/webroot/img/w3c_css.png: Cannot open: File exists
hotcakes/webroot/img/first.gif
tar: hotcakes/webroot/img/first.gif: Cannot open: File exists
hotcakes/webroot/img/not_active.png
tar: hotcakes/webroot/img/not_active.png: Cannot open: File exists
hotcakes/webroot/img/info.png
tar: hotcakes/webroot/img/info.png: Cannot open: File exists
hotcakes/webroot/img/chillispot.png
tar: hotcakes/webroot/img/chillispot.png: Cannot open: File exists
hotcakes/webroot/img/dialog-information.png
tar: hotcakes/webroot/img/dialog-information.png: Cannot open: File exists
hotcakes/webroot/img/close.png
tar: hotcakes/webroot/img/close.png: Cannot open: File exists
hotcakes/webroot/img/mikrotik.png
tar: hotcakes/webroot/img/mikrotik.png: Cannot open: File exists
hotcakes/webroot/img/wrt54g.jpg
tar: hotcakes/webroot/img/wrt54g.jpg: Cannot open: File exists
hotcakes/webroot/img/logo.jpg
tar: hotcakes/webroot/img/logo.jpg: Cannot open: File exists
hotcakes/webroot/img/r_active.png
tar: hotcakes/webroot/img/r_active.png: Cannot open: File exists
hotcakes/webroot/img/delete.png
tar: hotcakes/webroot/img/delete.png: Cannot open: File exists
hotcakes/webroot/img/stale.png
tar: hotcakes/webroot/img/stale.png: Cannot open: File exists
hotcakes/webroot/img/edit.png
tar: hotcakes/webroot/img/edit.png: Cannot open: File exists
hotcakes/webroot/img/u.gif
tar: hotcakes/webroot/img/u.gif: Cannot open: File exists
hotcakes/webroot/img/active.png
tar: hotcakes/webroot/img/active.png: Cannot open: File exists
hotcakes/webroot/img/ldap.png
tar: hotcakes/webroot/img/ldap.png: Cannot open: File exists
hotcakes/webroot/img/view.png
tar: hotcakes/webroot/img/view.png: Cannot open: File exists
hotcakes/webroot/img/kick.png
tar: hotcakes/webroot/img/kick.png: Cannot open: File exists
hotcakes/webroot/img/flags/
hotcakes/webroot/img/flags/ger.png
tar: hotcakes/webroot/img/flags/ger.png: Cannot open: File exists
hotcakes/webroot/img/flags/ken.png
tar: hotcakes/webroot/img/flags/ken.png: Cannot open: File exists
hotcakes/webroot/img/flags/sa.png
tar: hotcakes/webroot/img/flags/sa.png: Cannot open: File exists
hotcakes/webroot/img/flags/fran.png
tar: hotcakes/webroot/img/flags/fran.png: Cannot open: File exists
hotcakes/webroot/img/flags/braz.png
tar: hotcakes/webroot/img/flags/braz.png: Cannot open: File exists
hotcakes/webroot/img/passive.png
tar: hotcakes/webroot/img/flags: Cannot utime: Operation not permitted
tar: hotcakes/webroot/img/passive.png: Cannot open: File exists
hotcakes/webroot/img/clear.png
tar: hotcakes/webroot/img/clear.png: Cannot open: File exists
hotcakes/webroot/img/hotcakes.png
tar: hotcakes/webroot/img/hotcakes.png: Cannot open: File exists
hotcakes/webroot/img/previous.gif
tar: hotcakes/webroot/img/previous.gif: Cannot open: File exists
hotcakes/webroot/img/last.gif
tar: hotcakes/webroot/img/last.gif: Cannot open: File exists
hotcakes/webroot/img/logos/
hotcakes/webroot/img/logos/coffee.jpg
tar: hotcakes/webroot/img/logos/coffee.jpg: Cannot open: File exists
hotcakes/webroot/img/logos/burger.jpg
tar: hotcakes/webroot/img/logos/burger.jpg: Cannot open: File exists
hotcakes/webroot/css.php
tar: hotcakes/webroot/img/logos: Cannot utime: Operation not permitted
tar: hotcakes/webroot/img: Cannot utime: Operation not permitted
tar: hotcakes/webroot/css.php: Cannot open: File exists
hotcakes/webroot/files/
hotcakes/webroot/files/menu_c.php
tar: hotcakes/webroot/files/menu_c.php: Cannot open: File exists
hotcakes/webroot/files/radscenario_wip
tar: hotcakes/webroot/files/radscenario_wip: Cannot open: File exists
hotcakes/webroot/files/rules_for_user.pl
tar: hotcakes/webroot/files/rules_for_user.pl: Cannot open: File exists
hotcakes/webroot/files/menu_cashier.php
tar: hotcakes/webroot/files/menu_cashier.php: Cannot open: File exists
hotcakes/webroot/files/fetch_rules.sh
tar: hotcakes/webroot/files/fetch_rules.sh: Cannot open: File exists
hotcakes/webroot/files/menu.php
tar: hotcakes/webroot/files/menu.php: Cannot open: File exists
hotcakes/webroot/files/greenbox_start.php
tar: hotcakes/webroot/files/greenbox_start.php: Cannot open: File exists
hotcakes/webroot/files/clear_rules.sh
tar: hotcakes/webroot/files/clear_rules.sh: Cannot open: File exists
hotcakes/webroot/files/sidebar.php
tar: hotcakes/webroot/files/sidebar.php: Cannot open: File exists
hotcakes/webroot/files/client_links.php
tar: hotcakes/webroot/files/client_links.php: Cannot open: File exists
hotcakes/webroot/files/radpod
tar: hotcakes/webroot/files/radpod: Cannot open: File exists
hotcakes/webroot/files/greenbox_end.php
tar: hotcakes/webroot/files/greenbox_end.php: Cannot open: File exists
hotcakes/webroot/files/translations/
hotcakes/webroot/files/translations/messages.po
tar: hotcakes/webroot/files/translations/messages.po: Cannot open: File exists
hotcakes/webroot/files/translations/messages.mo
tar: hotcakes/webroot/files/translations/messages.mo: Cannot open: File exists
hotcakes/webroot/files/translations/create_po_file.pl
tar: hotcakes/webroot/files/translations/create_po_file.pl: Cannot open: File exists
hotcakes/webroot/images/
tar: hotcakes/webroot/files/translations: Cannot utime: Operation not permitted
tar: hotcakes/webroot/files: Cannot utime: Operation not permitted
hotcakes/webroot/images/img11.gif
tar: hotcakes/webroot/images/img11.gif: Cannot open: File exists
hotcakes/webroot/images/img16.gif
tar: hotcakes/webroot/images/img16.gif: Cannot open: File exists
hotcakes/webroot/images/img03.gif
tar: hotcakes/webroot/images/img03.gif: Cannot open: File exists
hotcakes/webroot/images/img08.gif
tar: hotcakes/webroot/images/img08.gif: Cannot open: File exists
hotcakes/webroot/images/img05.gif
tar: hotcakes/webroot/images/img05.gif: Cannot open: File exists
hotcakes/webroot/images/img07.gif
tar: hotcakes/webroot/images/img07.gif: Cannot open: File exists
hotcakes/webroot/images/img13.gif
tar: hotcakes/webroot/images/img13.gif: Cannot open: File exists
hotcakes/webroot/images/img02.gif
tar: hotcakes/webroot/images/img02.gif: Cannot open: File exists
hotcakes/webroot/images/img10.gif
tar: hotcakes/webroot/images/img10.gif: Cannot open: File exists
hotcakes/webroot/images/img06.gif
tar: hotcakes/webroot/images/img06.gif: Cannot open: File exists
hotcakes/webroot/images/img17.jpg
tar: hotcakes/webroot/images/img17.jpg: Cannot open: File exists
hotcakes/webroot/images/img12.gif
tar: hotcakes/webroot/images/img12.gif: Cannot open: File exists
hotcakes/webroot/images/img14.gif
tar: hotcakes/webroot/images/img14.gif: Cannot open: File exists
hotcakes/webroot/images/img01.gif
tar: hotcakes/webroot/images/img01.gif: Cannot open: File exists
hotcakes/webroot/images/img04.gif
tar: hotcakes/webroot/images/img04.gif: Cannot open: File exists
hotcakes/webroot/images/img09.gif
tar: hotcakes/webroot/images/img09.gif: Cannot open: File exists
hotcakes/webroot/images/spacer.gif
tar: hotcakes/webroot/images/spacer.gif: Cannot open: File exists
hotcakes/webroot/images/img15.gif
tar: hotcakes/webroot/images/img15.gif: Cannot open: File exists
hotcakes/controllers/
tar: hotcakes/webroot/images: Cannot utime: Operation not permitted
tar: hotcakes/webroot: Cannot utime: Operation not permitted
hotcakes/controllers/debit_orders_controller.php
tar: hotcakes/controllers/debit_orders_controller.php: Cannot open: File exists
hotcakes/controllers/prepaid_vouchers_controller.php
tar: hotcakes/controllers/prepaid_vouchers_controller.php: Cannot open: File exists
hotcakes/controllers/radaccts_controller.php
tar: hotcakes/controllers/radaccts_controller.php: Cannot open: File exists
hotcakes/controllers/permanent_users_controller.php
tar: hotcakes/controllers/permanent_users_controller.php: Cannot open: File exists
hotcakes/controllers/iptable_rules_controller.php
tar: hotcakes/controllers/iptable_rules_controller.php: Cannot open: File exists
hotcakes/controllers/attributes_controller.php
tar: hotcakes/controllers/attributes_controller.php: Cannot open: File exists
hotcakes/controllers/admins_controller.php
tar: hotcakes/controllers/admins_controller.php: Cannot open: File exists
hotcakes/controllers/billing_plans_controller.php
tar: hotcakes/controllers/billing_plans_controller.php: Cannot open: File exists
hotcakes/controllers/account_types_controller.php
tar: hotcakes/controllers/account_types_controller.php: Cannot open: File exists
hotcakes/controllers/invoices_controller.php
tar: hotcakes/controllers/invoices_controller.php: Cannot open: File exists
hotcakes/controllers/landing_pages_controller.php
tar: hotcakes/controllers/landing_pages_controller.php: Cannot open: File exists
hotcakes/controllers/nas_models_controller.php
tar: hotcakes/controllers/nas_models_controller.php: Cannot open: File exists
hotcakes/controllers/configuration_items_controller.php
tar: hotcakes/controllers/configuration_items_controller.php: Cannot open: File exists
hotcakes/controllers/extra_services_controller.php
tar: hotcakes/controllers/extra_services_controller.php: Cannot open: File exists
hotcakes/controllers/components/
hotcakes/controllers/components/radiusproxy.php
tar: hotcakes/controllers/components/radiusproxy.php: Cannot open: File exists
hotcakes/controllers/components/autocomplete_component.php
tar: hotcakes/controllers/components/autocomplete_component.php: Cannot open: File exists
hotcakes/controllers/components/autocomplete.php
tar: hotcakes/controllers/components/autocomplete.php: Cannot open: File exists
hotcakes/controllers/components/swift_mailer.php
tar: hotcakes/controllers/components/swift_mailer.php: Cannot open: File exists
hotcakes/controllers/components/pager.php
tar: hotcakes/controllers/components/pager.php: Cannot open: File exists
hotcakes/controllers/components/autocomplete_compontent.php
tar: hotcakes/controllers/components/autocomplete_compontent.php: Cannot open: File exists
hotcakes/controllers/components/rights.php
tar: hotcakes/controllers/components/rights.php: Cannot open: File exists
hotcakes/controllers/components/cashiers.php
tar: hotcakes/controllers/components/cashiers.php: Cannot open: File exists
hotcakes/controllers/status_lists_controller.php
tar: hotcakes/controllers/components: Cannot utime: Operation not permitted
tar: hotcakes/controllers/status_lists_controller.php: Cannot open: File exists
hotcakes/controllers/nas_types_controller.php
tar: hotcakes/controllers/nas_types_controller.php: Cannot open: File exists
hotcakes/controllers/radreplies_controller.php
tar: hotcakes/controllers/radreplies_controller.php: Cannot open: File exists
hotcakes/controllers/controlled_realms_controller.php
tar: hotcakes/controllers/controlled_realms_controller.php: Cannot open: File exists
hotcakes/controllers/realms_controller.php
tar: hotcakes/controllers/realms_controller.php: Cannot open: File exists
hotcakes/controllers/radgroupchecks_controller.php
tar: hotcakes/controllers/radgroupchecks_controller.php: Cannot open: File exists
hotcakes/controllers/radchecks_controller.php
tar: hotcakes/controllers/radchecks_controller.php: Cannot open: File exists
hotcakes/controllers/received_payments_controller.php
tar: hotcakes/controllers/received_payments_controller.php: Cannot open: File exists
hotcakes/controllers/support_calls_controller.php
tar: hotcakes/controllers/support_calls_controller.php: Cannot open: File exists
hotcakes/controllers/nas_controller.php
tar: hotcakes/controllers/nas_controller.php: Cannot open: File exists
hotcakes/controllers/payment_methods_controller.php
tar: hotcakes/controllers/payment_methods_controller.php: Cannot open: File exists
hotcakes/controllers/cashiers_controller.php
tar: hotcakes/controllers/cashiers_controller.php: Cannot open: File exists
hotcakes/controllers/banks_controller.php
tar: hotcakes/controllers/banks_controller.php: Cannot open: File exists
hotcakes/controllers/skelleton_profiles_controller.php
tar: hotcakes/controllers/skelleton_profiles_controller.php: Cannot open: File exists
hotcakes/controllers/pops_controller.php
tar: hotcakes/controllers/pops_controller.php: Cannot open: File exists
hotcakes/controllers/wisp_details_controller.php
tar: hotcakes/controllers/wisp_details_controller.php: Cannot open: File exists
hotcakes/config/
tar: hotcakes/controllers: Cannot utime: Operation not permitted
hotcakes/config/sql/
hotcakes/config/sql/sessions.sql
tar: hotcakes/config/sql/sessions.sql: Cannot open: File exists
hotcakes/config/sql/db_acl.sql
tar: hotcakes/config/sql/db_acl.sql: Cannot open: File exists
hotcakes/config/acl.ini.php
tar: hotcakes/config/sql: Cannot utime: Operation not permitted
tar: hotcakes/config/acl.ini.php: Cannot open: File exists
hotcakes/config/core.php
tar: hotcakes/config/core.php: Cannot open: File exists
hotcakes/config/database.php
tar: hotcakes/config/database.php: Cannot open: File exists
hotcakes/config/inflections.php
tar: hotcakes/config/inflections.php: Cannot open: File exists
hotcakes/config/bootstrap.php
tar: hotcakes/config/bootstrap.php: Cannot open: File exists
hotcakes/config/database.php.default
tar: hotcakes/config/database.php.default: Cannot open: File exists
hotcakes/config/routes.php
tar: hotcakes/config/routes.php: Cannot open: File exists
hotcakes/app_controller.php
tar: hotcakes/config: Cannot utime: Operation not permitted
tar: hotcakes/app_controller.php: Cannot open: File exists
hotcakes/plugins/
hotcakes/plugins/locale/
hotcakes/plugins/locale/pt_BR/
hotcakes/plugins/locale/pt_BR/LC_MESSAGES/
hotcakes/plugins/locale/pt_BR/LC_MESSAGES/messages.po
tar: hotcakes/plugins/locale/pt_BR/LC_MESSAGES/messages.po: Cannot open: File exists
hotcakes/plugins/locale/pt_BR/LC_MESSAGES/messages.mo
tar: hotcakes/plugins/locale/pt_BR/LC_MESSAGES/messages.mo: Cannot open: File exists
hotcakes/plugins/locale/af_ZA/
tar: hotcakes/plugins/locale/pt_BR/LC_MESSAGES: Cannot utime: Operation not permitted
tar: hotcakes/plugins/locale/pt_BR: Cannot utime: Operation not permitted
hotcakes/plugins/locale/af_ZA/LC_MESSAGES/
hotcakes/plugins/locale/af_ZA/LC_MESSAGES/messages.po
tar: hotcakes/plugins/locale/af_ZA/LC_MESSAGES/messages.po: Cannot open: File exists
hotcakes/plugins/locale/af_ZA/LC_MESSAGES/messages.po~
tar: hotcakes/plugins/locale/af_ZA/LC_MESSAGES/messages.po~: Cannot open: File exists
hotcakes/plugins/locale/af_ZA/LC_MESSAGES/messages.mo
tar: hotcakes/plugins/locale/af_ZA/LC_MESSAGES/messages.mo: Cannot open: File exists
hotcakes/plugins/locale/messages.po
tar: hotcakes/plugins/locale/af_ZA/LC_MESSAGES: Cannot utime: Operation not permitted
tar: hotcakes/plugins/locale/af_ZA: Cannot utime: Operation not permitted
tar: hotcakes/plugins/locale/messages.po: Cannot open: File exists
hotcakes/plugins/locale/de_BE/
hotcakes/plugins/locale/de_BE/LC_MESSAGES/
hotcakes/plugins/locale/de_BE/LC_MESSAGES/messages.po
tar: hotcakes/plugins/locale/de_BE/LC_MESSAGES/messages.po: Cannot open: File exists
hotcakes/plugins/locale/de_BE/LC_MESSAGES/messages.mo
tar: hotcakes/plugins/locale/de_BE/LC_MESSAGES/messages.mo: Cannot open: File exists
hotcakes/plugins/locale/fr_FR/
tar: hotcakes/plugins/locale/de_BE/LC_MESSAGES: Cannot utime: Operation not permitted
tar: hotcakes/plugins/locale/de_BE: Cannot utime: Operation not permitted
hotcakes/plugins/locale/fr_FR/LC_MESSAGES/
hotcakes/plugins/locale/fr_FR/LC_MESSAGES/messages.po
tar: hotcakes/plugins/locale/fr_FR/LC_MESSAGES/messages.po: Cannot open: File exists
hotcakes/plugins/locale/fr_FR/LC_MESSAGES/messages.mo
tar: hotcakes/plugins/locale/fr_FR/LC_MESSAGES/messages.mo: Cannot open: File exists
hotcakes/plugins/locale/en_GB/
tar: hotcakes/plugins/locale/fr_FR/LC_MESSAGES: Cannot utime: Operation not permitted
tar: hotcakes/plugins/locale/fr_FR: Cannot utime: Operation not permitted
hotcakes/plugins/locale/en_GB/LC_MESSAGES/
hotcakes/plugins/locale/en_GB/LC_MESSAGES/messages.po
tar: hotcakes/plugins/locale/en_GB/LC_MESSAGES/messages.po: Cannot open: File exists
hotcakes/plugins/locale/en_GB/LC_MESSAGES/messages.mo
tar: hotcakes/plugins/locale/en_GB/LC_MESSAGES/messages.mo: Cannot open: File exists
hotcakes/plugins/locale/en/
tar: hotcakes/plugins/locale/en_GB/LC_MESSAGES: Cannot utime: Operation not permitted
tar: hotcakes/plugins/locale/en_GB: Cannot utime: Operation not permitted
hotcakes/plugins/locale/en/LC_MESSAGES/
hotcakes/models/
tar: hotcakes/plugins/locale/en/LC_MESSAGES: Cannot utime: Operation not permitted
tar: hotcakes/plugins/locale/en: Cannot utime: Operation not permitted
tar: hotcakes/plugins/locale: Cannot utime: Operation not permitted
tar: hotcakes/plugins: Cannot utime: Operation not permitted
hotcakes/models/permission.php
tar: hotcakes/models/permission.php: Cannot open: File exists
hotcakes/models/nas_model.php
tar: hotcakes/models/nas_model.php: Cannot open: File exists
hotcakes/models/prepaid_voucher.php
tar: hotcakes/models/prepaid_voucher.php: Cannot open: File exists
hotcakes/models/radgroupreply.php
tar: hotcakes/models/radgroupreply.php: Cannot open: File exists
hotcakes/models/na.php
tar: hotcakes/models/na.php: Cannot open: File exists
hotcakes/models/location.php
tar: hotcakes/models/location.php: Cannot open: File exists
hotcakes/models/radgroupcheck.php
tar: hotcakes/models/radgroupcheck.php: Cannot open: File exists
hotcakes/models/group.php
tar: hotcakes/models/group.php: Cannot open: File exists
hotcakes/models/usergroup.php
tar: hotcakes/models/usergroup.php: Cannot open: File exists
hotcakes/models/billing_plan.php
tar: hotcakes/models/billing_plan.php: Cannot open: File exists
hotcakes/models/payment_method.php
tar: hotcakes/models/payment_method.php: Cannot open: File exists
hotcakes/models/admin.php
tar: hotcakes/models/admin.php: Cannot open: File exists
hotcakes/models/controlled_realm.php
tar: hotcakes/models/controlled_realm.php: Cannot open: File exists
hotcakes/models/radreply.php
tar: hotcakes/models/radreply.php: Cannot open: File exists
hotcakes/models/account_type.php
tar: hotcakes/models/account_type.php: Cannot open: File exists
hotcakes/models/permanent_user.php
tar: hotcakes/models/permanent_user.php: Cannot open: File exists
hotcakes/models/radcheck.php
tar: hotcakes/models/radcheck.php: Cannot open: File exists
hotcakes/models/behaviors/
hotcakes/models/nas_type.php
tar: hotcakes/models/behaviors: Cannot utime: Operation not permitted
tar: hotcakes/models/nas_type.php: Cannot open: File exists
hotcakes/models/support_call.php
tar: hotcakes/models/support_call.php: Cannot open: File exists
hotcakes/models/realm.php
tar: hotcakes/models/realm.php: Cannot open: File exists
hotcakes/models/debit_order.php
tar: hotcakes/models/debit_order.php: Cannot open: File exists
hotcakes/models/configuration_item.php
tar: hotcakes/models/configuration_item.php: Cannot open: File exists
hotcakes/models/pop.php
tar: hotcakes/models/pop.php: Cannot open: File exists
hotcakes/models/bank.php
tar: hotcakes/models/bank.php: Cannot open: File exists
hotcakes/models/invoice.php
tar: hotcakes/models/invoice.php: Cannot open: File exists
hotcakes/models/radacct.php
tar: hotcakes/models/radacct.php: Cannot open: File exists
hotcakes/models/attribute.php
tar: hotcakes/models/attribute.php: Cannot open: File exists
hotcakes/models/rad_group_check.php
tar: hotcakes/models/rad_group_check.php: Cannot open: File exists
hotcakes/models/extra_service.php
tar: hotcakes/models/extra_service.php: Cannot open: File exists
hotcakes/models/wisp_detail.php
tar: hotcakes/models/wisp_detail.php: Cannot open: File exists
hotcakes/models/cashier.php
tar: hotcakes/models/cashier.php: Cannot open: File exists
hotcakes/models/iptable_rule.php
tar: hotcakes/models/iptable_rule.php: Cannot open: File exists
hotcakes/models/status_list.php
tar: hotcakes/models/status_list.php: Cannot open: File exists
hotcakes/models/skelleton_profile.php
tar: hotcakes/models/skelleton_profile.php: Cannot open: File exists
hotcakes/models/received_payment.php
tar: hotcakes/models/received_payment.php: Cannot open: File exists
hotcakes/models/user.php
tar: hotcakes/models/user.php: Cannot open: File exists
hotcakes/models/radgcheck.php
tar: hotcakes/models/radgcheck.php: Cannot open: File exists
hotcakes/db/
tar: hotcakes/models: Cannot utime: Operation not permitted
hotcakes/db/index.php
tar: hotcakes/db/index.php: Cannot open: File exists
hotcakes/db/radius/
hotcakes/db/radius/sqlcounter.conf
tar: hotcakes/db/radius/sqlcounter.conf: Cannot open: File exists
hotcakes/db/radius/dictionary.chillispot
tar: hotcakes/db/radius/dictionary.chillispot: Cannot open: File exists
hotcakes/db/radius/sql.conf
tar: hotcakes/db/radius/sql.conf: Cannot open: File exists
hotcakes/db/radius/proxy.conf
tar: hotcakes/db/radius/proxy.conf: Cannot open: File exists
hotcakes/db/radius/rlm_perl.pm
tar: hotcakes/db/radius/rlm_perl.pm: Cannot open: File exists
hotcakes/db/radius/radiusd.conf
tar: hotcakes/db/radius/radiusd.conf: Cannot open: File exists
hotcakes/db/radius/users
tar: hotcakes/db/radius/users: Cannot open: File exists
hotcakes/db/radius/dictionary
tar: hotcakes/db/radius/dictionary: Cannot open: File exists
hotcakes/db/radius.sql
tar: hotcakes/db/radius: Cannot utime: Operation not permitted
tar: hotcakes/db/radius.sql: Cannot open: File exists
hotcakes/db/radius-beta-5patch.sql
tar: hotcakes/db/radius-beta-5patch.sql: Cannot open: File exists
tar: hotcakes/db: Cannot utime: Operation not permitted
tar: hotcakes: Cannot utime: Operation not permitted
tar: Error exit delayed from previous errors

---

### Post by madsmeg on 2008-09-18
Yeah, we really need a link to the site or somthing as i cant find this package.

If we have somthing to work from we can help you, also pastebin ([http://paste.ubuntu.com/](http://paste.ubuntu.com/)) the errors you are recieving and put a link to it in your next post.

Thanks

Mad

---

### Post by madsmeg on 2008-09-18
operation not permited.....

try putting 

sudo ./configure

sudo make

sudo make install

---

### Post by Tatty on 2008-09-18
can you also copy and paste the command you typed (including the command prompt) so we can see where you are and exactly what you typed.

---

### Post by nowshining on 2008-09-18
> **abennett said:**
> This is what I get when I run tar -zxvf again for the 9th time.



tar: hotcakes/webroot/doc/hotcakes_cookbook/x51.html: Cannot open: File exists
hotcakes/webroot/doc/hotcakes_cookbook/x258.html
tar: hotcakes/webroot/doc/hotcakes_cookbook/x258.html: Cannot open: File exists
hotcakes/webroot/doc/hotcakes_cookbook/x771.html
tar: hotcakes/webroot/doc/hotcakes_cookbook/x771.html: Cannot open: File exists
hotcakes/webroot/doc/hotcakes_cookbook/openwrt.odg
tar: hotcakes/webroot/doc/hotcakes_cookbook/openwrt.odg: Cannot open: File exists
hotcakes/webroot/doc/hotcakes_cookbook/images/
hotcakes/webroot/doc/hotcakes_cookbook/images/openwrt.png
tar: hotcakes/webroot/doc/hotcakes_cookbook/images/openwrt.png: Cannot open: File exists
hotcakes/webroot/doc/hotcakes_cookbook/images/nas_devices.png
tar: hotcakes/webroot/doc/hotcakes_cookbook/images/nas_devices.png: Cannot open: File exists
hotcakes/webroot/doc/hotcakes_cookbook/images/1.png
tar: hotcakes/webroot/doc/hotcakes_cookbook/images/1.png: Cannot open: File exists
hotcakes/webroot/doc/images/
tar: hotcakes/webroot/doc/hotcakes_cookbook/images: Cannot utime: Operation not permitted
tar: hotcakes/webroot/doc/hotcakes_cookbook: Cannot utime: Operation not permitted
hotcakes/webroot/doc/images/tip.gif
tar: hotcakes/webroot/doc/images/tip.gif: Cannot open: File exists
hotcakes/webroot/doc/images/warning.gif
tar: hotcakes/webroot/doc/images/warning.gif: Cannot open: File exists
hotcakes/webroot/doc/images/note.gif
tar: hotcakes/webroot/doc/images/note.gif: Cannot open: File exists
hotcakes/webroot/favicon.ico
tar: hotcakes/webroot/doc/images: Cannot utime: Operation not permitted
tar: hotcakes/webroot/doc: Cannot utime: Operation not permitted
tar: hotcakes/webroot/favicon.ico: Cannot open: File exists
hotcakes/webroot/generated/
hotcakes/webroot/img/
tar: hotcakes/webroot/generated: Cannot utime: Operation not permitted
hotcakes/webroot/img/acro.png
tar: hotcakes/webroot/img/acro.png: Cannot open: File exists
hotcakes/webroot/img/w3c_xhtml10.png
tar: hotcakes/webroot/img/w3c_xhtml10.png: Cannot open: File exists
hotcakes/webroot/img/menu/
hotcakes/webroot/img/menu/edit_user.png
tar: hotcakes/webroot/img/menu/edit_user.png: Cannot open: File exists
hotcakes/webroot/img/menu/help.png
tar: hotcakes/webroot/img/menu/help.png: Cannot open: File exists
hotcakes/webroot/img/menu/logout.png
tar: hotcakes/webroot/img/menu/logout.png: Cannot open: File exists
hotcakes/webroot/img/menu/documentation.png
tar: hotcakes/webroot/img/menu/documentation.png: Cannot open: File exists
hotcakes/webroot/img/menu/document.png
tar: hotcakes/webroot/img/menu/document.png: Cannot open: File exists
hotcakes/webroot/img/menu/user_permanent.png
tar: hotcakes/webroot/img/menu/user_permanent.png: Cannot open: File exists
hotcakes/webroot/img/menu/hotcakes.png
tar: hotcakes/webroot/img/menu/hotcakes.png: Cannot open: File exists
hotcakes/webroot/img/mail.png
tar: hotcakes/webroot/img/menu: Cannot utime: Operation not permitted
tar: hotcakes/webroot/img/mail.png: Cannot open: File exists
hotcakes/webroot/img/nas_generic.gif
tar: hotcakes/webroot/img/nas_generic.gif: Cannot open: File exists
hotcakes/webroot/img/d.gif
tar: hotcakes/webroot/img/d.gif: Cannot open: File exists
hotcakes/webroot/img/cake.power.png
tar: hotcakes/webroot/img/cake.power.png: Cannot open: File exists
hotcakes/webroot/img/next.gif
tar: hotcakes/webroot/img/next.gif: Cannot open: File exists
hotcakes/webroot/img/w3c_css.png
tar: hotcakes/webroot/img/w3c_css.png: Cannot open: File exists
hotcakes/webroot/img/first.gif
tar: hotcakes/webroot/img/first.gif: Cannot open: File exists
hotcakes/webroot/img/not_active.png
tar: hotcakes/webroot/img/not_active.png: Cannot open: File exists
hotcakes/webroot/img/info.png
tar: hotcakes/webroot/img/info.png: Cannot open: File exists
hotcakes/webroot/img/chillispot.png
tar: hotcakes/webroot/img/chillispot.png: Cannot open: File exists
hotcakes/webroot/img/dialog-information.png
tar: hotcakes/webroot/img/dialog-information.png: Cannot open: File exists
hotcakes/webroot/img/close.png
tar: hotcakes/webroot/img/close.png: Cannot open: File exists
hotcakes/webroot/img/mikrotik.png
tar: hotcakes/webroot/img/mikrotik.png: Cannot open: File exists
hotcakes/webroot/img/wrt54g.jpg
tar: hotcakes/webroot/img/wrt54g.jpg: Cannot open: File exists
hotcakes/webroot/img/logo.jpg
tar: hotcakes/webroot/img/logo.jpg: Cannot open: File exists
hotcakes/webroot/img/r_active.png
tar: hotcakes/webroot/img/r_active.png: Cannot open: File exists
hotcakes/webroot/img/delete.png
tar: hotcakes/webroot/img/delete.png: Cannot open: File exists
hotcakes/webroot/img/stale.png
tar: hotcakes/webroot/img/stale.png: Cannot open: File exists
hotcakes/webroot/img/edit.png
tar: hotcakes/webroot/img/edit.png: Cannot open: File exists
hotcakes/webroot/img/u.gif
tar: hotcakes/webroot/img/u.gif: Cannot open: File exists
hotcakes/webroot/img/active.png
tar: hotcakes/webroot/img/active.png: Cannot open: File exists
hotcakes/webroot/img/ldap.png
tar: hotcakes/webroot/img/ldap.png: Cannot open: File exists
hotcakes/webroot/img/view.png
tar: hotcakes/webroot/img/view.png: Cannot open: File exists
hotcakes/webroot/img/kick.png
tar: hotcakes/webroot/img/kick.png: Cannot open: File exists
hotcakes/webroot/img/flags/
hotcakes/webroot/img/flags/ger.png
tar: hotcakes/webroot/img/flags/ger.png: Cannot open: File exists
hotcakes/webroot/img/flags/ken.png
tar: hotcakes/webroot/img/flags/ken.png: Cannot open: File exists
hotcakes/webroot/img/flags/sa.png
tar: hotcakes/webroot/img/flags/sa.png: Cannot open: File exists
hotcakes/webroot/img/flags/fran.png
tar: hotcakes/webroot/img/flags/fran.png: Cannot open: File exists
hotcakes/webroot/img/flags/braz.png
tar: hotcakes/webroot/img/flags/braz.png: Cannot open: File exists
hotcakes/webroot/img/passive.png
tar: hotcakes/webroot/img/flags: Cannot utime: Operation not permitted
tar: hotcakes/webroot/img/passive.png: Cannot open: File exists
hotcakes/webroot/img/clear.png
tar: hotcakes/webroot/img/clear.png: Cannot open: File exists
hotcakes/webroot/img/hotcakes.png
tar: hotcakes/webroot/img/hotcakes.png: Cannot open: File exists
hotcakes/webroot/img/previous.gif
tar: hotcakes/webroot/img/previous.gif: Cannot open: File exists
hotcakes/webroot/img/last.gif
tar: hotcakes/webroot/img/last.gif: Cannot open: File exists
hotcakes/webroot/img/logos/
hotcakes/webroot/img/logos/coffee.jpg
tar: hotcakes/webroot/img/logos/coffee.jpg: Cannot open: File exists
hotcakes/webroot/img/logos/burger.jpg
tar: hotcakes/webroot/img/logos/burger.jpg: Cannot open: File exists
hotcakes/webroot/css.php
tar: hotcakes/webroot/img/logos: Cannot utime: Operation not permitted
tar: hotcakes/webroot/img: Cannot utime: Operation not permitted
tar: hotcakes/webroot/css.php: Cannot open: File exists
hotcakes/webroot/files/
hotcakes/webroot/files/menu_c.php
tar: hotcakes/webroot/files/menu_c.php: Cannot open: File exists
hotcakes/webroot/files/radscenario_wip
tar: hotcakes/webroot/files/radscenario_wip: Cannot open: File exists
hotcakes/webroot/files/rules_for_user.pl
tar: hotcakes/webroot/files/rules_for_user.pl: Cannot open: File exists
hotcakes/webroot/files/menu_cashier.php
tar: hotcakes/webroot/files/menu_cashier.php: Cannot open: File exists
hotcakes/webroot/files/fetch_rules.sh
tar: hotcakes/webroot/files/fetch_rules.sh: Cannot open: File exists
hotcakes/webroot/files/menu.php
tar: hotcakes/webroot/files/menu.php: Cannot open: File exists
hotcakes/webroot/files/greenbox_start.php
tar: hotcakes/webroot/files/greenbox_start.php: Cannot open: File exists
hotcakes/webroot/files/clear_rules.sh
tar: hotcakes/webroot/files/clear_rules.sh: Cannot open: File exists
hotcakes/webroot/files/sidebar.php
tar: hotcakes/webroot/files/sidebar.php: Cannot open: File exists
hotcakes/webroot/files/client_links.php
tar: hotcakes/webroot/files/client_links.php: Cannot open: File exists
hotcakes/webroot/files/radpod
tar: hotcakes/webroot/files/radpod: Cannot open: File exists
hotcakes/webroot/files/greenbox_end.php
tar: hotcakes/webroot/files/greenbox_end.php: Cannot open: File exists
hotcakes/webroot/files/translations/
hotcakes/webroot/files/translations/messages.po
tar: hotcakes/webroot/files/translations/messages.po: Cannot open: File exists
hotcakes/webroot/files/translations/messages.mo
tar: hotcakes/webroot/files/translations/messages.mo: Cannot open: File exists
hotcakes/webroot/files/translations/create_po_file.pl
tar: hotcakes/webroot/files/translations/create_po_file.pl: Cannot open: File exists
hotcakes/webroot/images/
tar: hotcakes/webroot/files/translations: Cannot utime: Operation not permitted
tar: hotcakes/webroot/files: Cannot utime: Operation not permitted
hotcakes/webroot/images/img11.gif
tar: hotcakes/webroot/images/img11.gif: Cannot open: File exists
hotcakes/webroot/images/img16.gif
tar: hotcakes/webroot/images/img16.gif: Cannot open: File exists
hotcakes/webroot/images/img03.gif
tar: hotcakes/webroot/images/img03.gif: Cannot open: File exists
hotcakes/webroot/images/img08.gif
tar: hotcakes/webroot/images/img08.gif: Cannot open: File exists
hotcakes/webroot/images/img05.gif
tar: hotcakes/webroot/images/img05.gif: Cannot open: File exists
hotcakes/webroot/images/img07.gif
tar: hotcakes/webroot/images/img07.gif: Cannot open: File exists
hotcakes/webroot/images/img13.gif
tar: hotcakes/webroot/images/img13.gif: Cannot open: File exists
hotcakes/webroot/images/img02.gif
tar: hotcakes/webroot/images/img02.gif: Cannot open: File exists
hotcakes/webroot/images/img10.gif
tar: hotcakes/webroot/images/img10.gif: Cannot open: File exists
hotcakes/webroot/images/img06.gif
tar: hotcakes/webroot/images/img06.gif: Cannot open: File exists
hotcakes/webroot/images/img17.jpg
tar: hotcakes/webroot/images/img17.jpg: Cannot open: File exists
hotcakes/webroot/images/img12.gif
tar: hotcakes/webroot/images/img12.gif: Cannot open: File exists
hotcakes/webroot/images/img14.gif
tar: hotcakes/webroot/images/img14.gif: Cannot open: File exists
hotcakes/webroot/images/img01.gif
tar: hotcakes/webroot/images/img01.gif: Cannot open: File exists
hotcakes/webroot/images/img04.gif
tar: hotcakes/webroot/images/img04.gif: Cannot open: File exists
hotcakes/webroot/images/img09.gif
tar: hotcakes/webroot/images/img09.gif: Cannot open: File exists
hotcakes/webroot/images/spacer.gif
tar: hotcakes/webroot/images/spacer.gif: Cannot open: File exists
hotcakes/webroot/images/img15.gif
tar: hotcakes/webroot/images/img15.gif: Cannot open: File exists
hotcakes/controllers/
tar: hotcakes/webroot/images: Cannot utime: Operation not permitted
tar: hotcakes/webroot: Cannot utime: Operation not permitted
hotcakes/controllers/debit_orders_controller.php
tar: hotcakes/controllers/debit_orders_controller.php: Cannot open: File exists
hotcakes/controllers/prepaid_vouchers_controller.php
tar: hotcakes/controllers/prepaid_vouchers_controller.php: Cannot open: File exists
hotcakes/controllers/radaccts_controller.php
tar: hotcakes/controllers/radaccts_controller.php: Cannot open: File exists
hotcakes/controllers/permanent_users_controller.php
tar: hotcakes/controllers/permanent_users_controller.php: Cannot open: File exists
hotcakes/controllers/iptable_rules_controller.php
tar: hotcakes/controllers/iptable_rules_controller.php: Cannot open: File exists
hotcakes/controllers/attributes_controller.php
tar: hotcakes/controllers/attributes_controller.php: Cannot open: File exists
hotcakes/controllers/admins_controller.php
tar: hotcakes/controllers/admins_controller.php: Cannot open: File exists
hotcakes/controllers/billing_plans_controller.php
tar: hotcakes/controllers/billing_plans_controller.php: Cannot open: File exists
hotcakes/controllers/account_types_controller.php
tar: hotcakes/controllers/account_types_controller.php: Cannot open: File exists
hotcakes/controllers/invoices_controller.php
tar: hotcakes/controllers/invoices_controller.php: Cannot open: File exists
hotcakes/controllers/landing_pages_controller.php
tar: hotcakes/controllers/landing_pages_controller.php: Cannot open: File exists
hotcakes/controllers/nas_models_controller.php
tar: hotcakes/controllers/nas_models_controller.php: Cannot open: File exists
hotcakes/controllers/configuration_items_controller.php
tar: hotcakes/controllers/configuration_items_controller.php: Cannot open: File exists
hotcakes/controllers/extra_services_controller.php
tar: hotcakes/controllers/extra_services_controller.php: Cannot open: File exists
hotcakes/controllers/components/
hotcakes/controllers/components/radiusproxy.php
tar: hotcakes/controllers/components/radiusproxy.php: Cannot open: File exists
hotcakes/controllers/components/autocomplete_component.php
tar: hotcakes/controllers/components/autocomplete_component.php: Cannot open: File exists
hotcakes/controllers/components/autocomplete.php
tar: hotcakes/controllers/components/autocomplete.php: Cannot open: File exists
hotcakes/controllers/components/swift_mailer.php
tar: hotcakes/controllers/components/swift_mailer.php: Cannot open: File exists
hotcakes/controllers/components/pager.php
tar: hotcakes/controllers/components/pager.php: Cannot open: File exists
hotcakes/controllers/components/autocomplete_compontent.php
tar: hotcakes/controllers/components/autocomplete_compontent.php: Cannot open: File exists
hotcakes/controllers/components/rights.php
tar: hotcakes/controllers/components/rights.php: Cannot open: File exists
hotcakes/controllers/components/cashiers.php
tar: hotcakes/controllers/components/cashiers.php: Cannot open: File exists
hotcakes/controllers/status_lists_controller.php
tar: hotcakes/controllers/components: Cannot utime: Operation not permitted
tar: hotcakes/controllers/status_lists_controller.php: Cannot open: File exists
hotcakes/controllers/nas_types_controller.php
tar: hotcakes/controllers/nas_types_controller.php: Cannot open: File exists
hotcakes/controllers/radreplies_controller.php
tar: hotcakes/controllers/radreplies_controller.php: Cannot open: File exists
hotcakes/controllers/controlled_realms_controller.php
tar: hotcakes/controllers/controlled_realms_controller.php: Cannot open: File exists
hotcakes/controllers/realms_controller.php
tar: hotcakes/controllers/realms_controller.php: Cannot open: File exists
hotcakes/controllers/radgroupchecks_controller.php
tar: hotcakes/controllers/radgroupchecks_controller.php: Cannot open: File exists
hotcakes/controllers/radchecks_controller.php
tar: hotcakes/controllers/radchecks_controller.php: Cannot open: File exists
hotcakes/controllers/received_payments_controller.php
tar: hotcakes/controllers/received_payments_controller.php: Cannot open: File exists
hotcakes/controllers/support_calls_controller.php
tar: hotcakes/controllers/support_calls_controller.php: Cannot open: File exists
hotcakes/controllers/nas_controller.php
tar: hotcakes/controllers/nas_controller.php: Cannot open: File exists
hotcakes/controllers/payment_methods_controller.php
tar: hotcakes/controllers/payment_methods_controller.php: Cannot open: File exists
hotcakes/controllers/cashiers_controller.php
tar: hotcakes/controllers/cashiers_controller.php: Cannot open: File exists
hotcakes/controllers/banks_controller.php
tar: hotcakes/controllers/banks_controller.php: Cannot open: File exists
hotcakes/controllers/skelleton_profiles_controller.php
tar: hotcakes/controllers/skelleton_profiles_controller.php: Cannot open: File exists
hotcakes/controllers/pops_controller.php
tar: hotcakes/controllers/pops_controller.php: Cannot open: File exists
hotcakes/controllers/wisp_details_controller.php
tar: hotcakes/controllers/wisp_details_controller.php: Cannot open: File exists
hotcakes/config/
tar: hotcakes/controllers: Cannot utime: Operation not permitted
hotcakes/config/sql/
hotcakes/config/sql/sessions.sql
tar: hotcakes/config/sql/sessions.sql: Cannot open: File exists
hotcakes/config/sql/db_acl.sql
tar: hotcakes/config/sql/db_acl.sql: Cannot open: File exists
hotcakes/config/acl.ini.php
tar: hotcakes/config/sql: Cannot utime: Operation not permitted
tar: hotcakes/config/acl.ini.php: Cannot open: File exists
hotcakes/config/core.php
tar: hotcakes/config/core.php: Cannot open: File exists
hotcakes/config/database.php
tar: hotcakes/config/database.php: Cannot open: File exists
hotcakes/config/inflections.php
tar: hotcakes/config/inflections.php: Cannot open: File exists
hotcakes/config/bootstrap.php
tar: hotcakes/config/bootstrap.php: Cannot open: File exists
hotcakes/config/database.php.default
tar: hotcakes/config/database.php.default: Cannot open: File exists
hotcakes/config/routes.php
tar: hotcakes/config/routes.php: Cannot open: File exists
hotcakes/app_controller.php
tar: hotcakes/config: Cannot utime: Operation not permitted
tar: hotcakes/app_controller.php: Cannot open: File exists
hotcakes/plugins/
hotcakes/plugins/locale/
hotcakes/plugins/locale/pt_BR/
hotcakes/plugins/locale/pt_BR/LC_MESSAGES/
hotcakes/plugins/locale/pt_BR/LC_MESSAGES/messages.po
tar: hotcakes/plugins/locale/pt_BR/LC_MESSAGES/messages.po: Cannot open: File exists
hotcakes/plugins/locale/pt_BR/LC_MESSAGES/messages.mo
tar: hotcakes/plugins/locale/pt_BR/LC_MESSAGES/messages.mo: Cannot open: File exists
hotcakes/plugins/locale/af_ZA/
tar: hotcakes/plugins/locale/pt_BR/LC_MESSAGES: Cannot utime: Operation not permitted
tar: hotcakes/plugins/locale/pt_BR: Cannot utime: Operation not permitted
hotcakes/plugins/locale/af_ZA/LC_MESSAGES/
hotcakes/plugins/locale/af_ZA/LC_MESSAGES/messages.po
tar: hotcakes/plugins/locale/af_ZA/LC_MESSAGES/messages.po: Cannot open: File exists
hotcakes/plugins/locale/af_ZA/LC_MESSAGES/messages.po~
tar: hotcakes/plugins/locale/af_ZA/LC_MESSAGES/messages.po~: Cannot open: File exists
hotcakes/plugins/locale/af_ZA/LC_MESSAGES/messages.mo
tar: hotcakes/plugins/locale/af_ZA/LC_MESSAGES/messages.mo: Cannot open: File exists
hotcakes/plugins/locale/messages.po
tar: hotcakes/plugins/locale/af_ZA/LC_MESSAGES: Cannot utime: Operation not permitted
tar: hotcakes/plugins/locale/af_ZA: Cannot utime: Operation not permitted
tar: hotcakes/plugins/locale/messages.po: Cannot open: File exists
hotcakes/plugins/locale/de_BE/
hotcakes/plugins/locale/de_BE/LC_MESSAGES/
hotcakes/plugins/locale/de_BE/LC_MESSAGES/messages.po
tar: hotcakes/plugins/locale/de_BE/LC_MESSAGES/messages.po: Cannot open: File exists
hotcakes/plugins/locale/de_BE/LC_MESSAGES/messages.mo
tar: hotcakes/plugins/locale/de_BE/LC_MESSAGES/messages.mo: Cannot open: File exists
hotcakes/plugins/locale/fr_FR/
tar: hotcakes/plugins/locale/de_BE/LC_MESSAGES: Cannot utime: Operation not permitted
tar: hotcakes/plugins/locale/de_BE: Cannot utime: Operation not permitted
hotcakes/plugins/locale/fr_FR/LC_MESSAGES/
hotcakes/plugins/locale/fr_FR/LC_MESSAGES/messages.po
tar: hotcakes/plugins/locale/fr_FR/LC_MESSAGES/messages.po: Cannot open: File exists
hotcakes/plugins/locale/fr_FR/LC_MESSAGES/messages.mo
tar: hotcakes/plugins/locale/fr_FR/LC_MESSAGES/messages.mo: Cannot open: File exists
hotcakes/plugins/locale/en_GB/
tar: hotcakes/plugins/locale/fr_FR/LC_MESSAGES: Cannot utime: Operation not permitted
tar: hotcakes/plugins/locale/fr_FR: Cannot utime: Operation not permitted
hotcakes/plugins/locale/en_GB/LC_MESSAGES/
hotcakes/plugins/locale/en_GB/LC_MESSAGES/messages.po
tar: hotcakes/plugins/locale/en_GB/LC_MESSAGES/messages.po: Cannot open: File exists
hotcakes/plugins/locale/en_GB/LC_MESSAGES/messages.mo
tar: hotcakes/plugins/locale/en_GB/LC_MESSAGES/messages.mo: Cannot open: File exists
hotcakes/plugins/locale/en/
tar: hotcakes/plugins/locale/en_GB/LC_MESSAGES: Cannot utime: Operation not permitted
tar: hotcakes/plugins/locale/en_GB: Cannot utime: Operation not permitted
hotcakes/plugins/locale/en/LC_MESSAGES/
hotcakes/models/
tar: hotcakes/plugins/locale/en/LC_MESSAGES: Cannot utime: Operation not permitted
tar: hotcakes/plugins/locale/en: Cannot utime: Operation not permitted
tar: hotcakes/plugins/locale: Cannot utime: Operation not permitted
tar: hotcakes/plugins: Cannot utime: Operation not permitted
hotcakes/models/permission.php
tar: hotcakes/models/permission.php: Cannot open: File exists
hotcakes/models/nas_model.php
tar: hotcakes/models/nas_model.php: Cannot open: File exists
hotcakes/models/prepaid_voucher.php
tar: hotcakes/models/prepaid_voucher.php: Cannot open: File exists
hotcakes/models/radgroupreply.php
tar: hotcakes/models/radgroupreply.php: Cannot open: File exists
hotcakes/models/na.php
tar: hotcakes/models/na.php: Cannot open: File exists
hotcakes/models/location.php
tar: hotcakes/models/location.php: Cannot open: File exists
hotcakes/models/radgroupcheck.php
tar: hotcakes/models/radgroupcheck.php: Cannot open: File exists
hotcakes/models/group.php
tar: hotcakes/models/group.php: Cannot open: File exists
hotcakes/models/usergroup.php
tar: hotcakes/models/usergroup.php: Cannot open: File exists
hotcakes/models/billing_plan.php
tar: hotcakes/models/billing_plan.php: Cannot open: File exists
hotcakes/models/payment_method.php
tar: hotcakes/models/payment_method.php: Cannot open: File exists
hotcakes/models/admin.php
tar: hotcakes/models/admin.php: Cannot open: File exists
hotcakes/models/controlled_realm.php
tar: hotcakes/models/controlled_realm.php: Cannot open: File exists
hotcakes/models/radreply.php
tar: hotcakes/models/radreply.php: Cannot open: File exists
hotcakes/models/account_type.php
tar: hotcakes/models/account_type.php: Cannot open: File exists
hotcakes/models/permanent_user.php
tar: hotcakes/models/permanent_user.php: Cannot open: File exists
hotcakes/models/radcheck.php
tar: hotcakes/models/radcheck.php: Cannot open: File exists
hotcakes/models/behaviors/
hotcakes/models/nas_type.php
tar: hotcakes/models/behaviors: Cannot utime: Operation not permitted
tar: hotcakes/models/nas_type.php: Cannot open: File exists
hotcakes/models/support_call.php
tar: hotcakes/models/support_call.php: Cannot open: File exists
hotcakes/models/realm.php
tar: hotcakes/models/realm.php: Cannot open: File exists
hotcakes/models/debit_order.php
tar: hotcakes/models/debit_order.php: Cannot open: File exists
hotcakes/models/configuration_item.php
tar: hotcakes/models/configuration_item.php: Cannot open: File exists
hotcakes/models/pop.php
tar: hotcakes/models/pop.php: Cannot open: File exists
hotcakes/models/bank.php
tar: hotcakes/models/bank.php: Cannot open: File exists
hotcakes/models/invoice.php
tar: hotcakes/models/invoice.php: Cannot open: File exists
hotcakes/models/radacct.php
tar: hotcakes/models/radacct.php: Cannot open: File exists
hotcakes/models/attribute.php
tar: hotcakes/models/attribute.php: Cannot open: File exists
hotcakes/models/rad_group_check.php
tar: hotcakes/models/rad_group_check.php: Cannot open: File exists
hotcakes/models/extra_service.php
tar: hotcakes/models/extra_service.php: Cannot open: File exists
hotcakes/models/wisp_detail.php
tar: hotcakes/models/wisp_detail.php: Cannot open: File exists
hotcakes/models/cashier.php
tar: hotcakes/models/cashier.php: Cannot open: File exists
hotcakes/models/iptable_rule.php
tar: hotcakes/models/iptable_rule.php: Cannot open: File exists
hotcakes/models/status_list.php
tar: hotcakes/models/status_list.php: Cannot open: File exists
hotcakes/models/skelleton_profile.php
tar: hotcakes/models/skelleton_profile.php: Cannot open: File exists
hotcakes/models/received_payment.php
tar: hotcakes/models/received_payment.php: Cannot open: File exists
hotcakes/models/user.php
tar: hotcakes/models/user.php: Cannot open: File exists
hotcakes/models/radgcheck.php
tar: hotcakes/models/radgcheck.php: Cannot open: File exists
hotcakes/db/
tar: hotcakes/models: Cannot utime: Operation not permitted
hotcakes/db/index.php
tar: hotcakes/db/index.php: Cannot open: File exists
hotcakes/db/radius/
hotcakes/db/radius/sqlcounter.conf
tar: hotcakes/db/radius/sqlcounter.conf: Cannot open: File exists
hotcakes/db/radius/dictionary.chillispot
tar: hotcakes/db/radius/dictionary.chillispot: Cannot open: File exists
hotcakes/db/radius/sql.conf
tar: hotcakes/db/radius/sql.conf: Cannot open: File exists
hotcakes/db/radius/proxy.conf
tar: hotcakes/db/radius/proxy.conf: Cannot open: File exists
hotcakes/db/radius/rlm_perl.pm
tar: hotcakes/db/radius/rlm_perl.pm: Cannot open: File exists
hotcakes/db/radius/radiusd.conf
tar: hotcakes/db/radius/radiusd.conf: Cannot open: File exists
hotcakes/db/radius/users
tar: hotcakes/db/radius/users: Cannot open: File exists
hotcakes/db/radius/dictionary
tar: hotcakes/db/radius/dictionary: Cannot open: File exists
hotcakes/db/radius.sql
tar: hotcakes/db/radius: Cannot utime: Operation not permitted
tar: hotcakes/db/radius.sql: Cannot open: File exists
hotcakes/db/radius-beta-5patch.sql
tar: hotcakes/db/radius-beta-5patch.sql: Cannot open: File exists
tar: hotcakes/db: Cannot utime: Operation not permitted
tar: hotcakes: Cannot utime: Operation not permitted
tar: Error exit delayed from previous errors

it's already untared as i can see, cd into the untared directory now and do ./configure and if that doesn't work try a src folder or better yet did you open the readme and or install txt file to read it?? They usually won't have any extensions but the program such as gedit should open em' straight up...

---

### Post by abennett on 2008-09-18
Here is the URL [http://sourceforge.net/projects/hotcakes/](http://sourceforge.net/projects/hotcakes/)

---

### Post by madsmeg on 2008-09-18
Also please dont post that much code at one time, please use [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by abennett on 2008-09-18
This is all it says in the README file and it does not have a Install file.
9 November 2007 (12:49)
---------------------------------------------------
--Welcome to this fith Beta Release of Hotcakes.-
---------------------------------------------------
Hotcakes release 01-05 (Beta-5)

Hotcakes is a Hotspot management system.

It is a working solution, but still in the early stages.
You are more than welcome to give it a try.

Beta-5 has alot of new features.

1.) It has multiple access levels (Admin, Cashier, Client)
2.) Multi language support
3.) Improved documentation
4.) User Interface Improvements

If you are looking for Documentation - You are in for a pleasant surprise!

YES THERE ARE :-)!!!!!

There is a setup HOWTO under the 'webroot/doc/hotcakes_setup_guide/' directory.
...and all the main web-pages you will use contain inline help.

Hope you've got your Ubuntu machine with two network cards up and ready.
(other distro's should be just as easy to set up)

See you over at the HOWTO.

/*
Copyright (c) <2007> <dirkvanderwalt> (<dirkvanderwalt at gmail dot com>).

    This program is free software; you can redistribute it and/or modify
    it under the terms of the GNU General Public License as published by
    the Free Software Foundation; either version 2 of the License, or
    (at your option) any later version.

    This program is distributed in the hope that it will be useful,
    but WITHOUT ANY WARRANTY; without even the implied warranty of
    MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
    GNU General Public License for more details.

    You should have received a copy of the GNU General Public License
    along with this program; if not, write to the Free Software
    Foundation, Inc., 51 Franklin St, Fifth Floor, Boston, MA  02110-1301  USA
*/

---

### Post by abennett on 2008-09-18
Sorry. Frist timer. didnt know....

---

### Post by Tatty on 2008-09-18
did you try going here?
> 
There is a setup HOWTO under the 'webroot/doc/hotcakes_setup_guide/' directory.

---

### Post by madsmeg on 2008-09-18
heh not having a go, just pointing out

---

### Post by abennett on 2008-09-18
> **Tatty said:**
> did you try going here?
Yes. Didnt look like anything to click on that would help me.

---

### Post by madsmeg on 2008-09-18
It looks from the link you may have to have MySQL and PHP setup, silly question, but are they?

EDIT: Though i may be wrong

---

### Post by abennett on 2008-09-18
> **madsmeg said:**
> It looks from the link you may have to have MySQL and PHP setup, silly question, but are they?

EDIT: Though i may be wrong
Not really knowing what Im doing I will guess "no". Ill try to check and see, but I cant gaurantee I will be able to do that for you...

---

### Post by Tatty on 2008-09-18
I just downloaded the .tar.gz,  it appears that there is nothing you need to compile, just extract it and run it.

If you go to that directory indicated in the readme (webroot/doc/hotcakes_setup_guide/), there is dome documentation which should get you going.  Just load the index.html file and the manual should appear in firefox.

---

### Post by madsmeg on 2008-09-18
why is it always somthing simple :p

---

### Post by abennett on 2008-09-18
> **madsmeg said:**
> why is it always somthing simple :p
Simple.. Ahhhhhhhhhh. What the hell is a dome documentation? i go to the folder and click on the hotcakes setup guide and then what?

---

### Post by nowshining on 2008-09-18
read it :) and follow the instructions...

---

### Post by Tatty on 2008-09-18
> **abennett said:**
> Simple.. Ahhhhhhhhhh. What the hell is a dome documentation? i go to the folder and click on the hotcakes setup guide and then what?

If you double click the index.html file then it will open the setup guide in firefox.  There is actually a specific section in it for ubuntu 7.10, which should give you a good starting point.

Im still not quite sure exactly what this app is, but it seems pretty deep (the readme file says you need two network cards), so you may want to have a careful read of the documentation.

---

### Post by abennett on 2008-09-18
> **Tatty said:**
> If you double click the index.html file then it will open the setup guide in firefox.  There is actually a specific section in it for ubuntu 7.10, which should give you a good starting point.

Im still not quite sure exactly what this app is, but it seems pretty deep (the readme file says you need two network cards), so you may want to have a careful read of the documentation.
Thank you for the help. Found that index.html file and started reading.. Cant wait to figure out all the **** that that has to say. I hate being a newbie.

---

### Post by Tatty on 2008-09-18
> **abennett said:**
> Thank you for the help. Found that index.html file and started reading.. Cant wait to figure out all the **** that that has to say. I hate being a newbie.

Theres ALWAYS something new to learn  ;)

Good luck with hotcakes!

---

