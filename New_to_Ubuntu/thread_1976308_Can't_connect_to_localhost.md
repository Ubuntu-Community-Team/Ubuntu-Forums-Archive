---
title: "Can't connect to localhost"
date: 2012-05-08
forum: New to Ubuntu
---

### Post by geomcd1949 on 2012-05-08
I recently upgraded from 12.04 Beta to 12.04 LTS. When I use my browser (Firefox or Chromium) to try to access localhost, I get a message saying Unable to Connect. I had no problems before upgrading. Help is appreciated!

~George

---

### Post by plucky on 2012-05-09
> **geomcd1949 said:**
> I recently upgraded from 12.04 Beta to 12.04 LTS. When I use my browser (Firefox or Chromium) to try to access localhost, I get a message saying Unable to Connect. I had no problems before upgrading. Help is appreciated!

~George

What are you trying to access on "localhost"?

By the way I get the same error on 10.04.4 LTS

---

### Post by zeljkojagust on 2012-05-09
Could you please execute the following command in terminal and paste the output here:
```
sudo netstat -apn
```

---

### Post by geomcd1949 on 2012-05-09
Sent readout from the wrong machine. Will post from correct machine momentarily. Sorry.

---

### Post by geomcd1949 on 2012-05-09
> **plucky said:**
> What are you trying to access on "localhost"?

By the way I get the same error on 10.04.4 LTS

I use localhost view .php web pages on my own machine. Files are kept in /var/www/--- for which I've properly set the permissions.

Localhost worked fine until I upgraded from 12.04 beta to 12.04 LTS.

Thanks!

~George

---

### Post by kellemes on 2012-05-09
Apache is running?
```
sudo /etc/init.d/apache2 restart
```

---

### Post by geomcd1949 on 2012-05-09
/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12251    2056/goa-daemon     
unix  2      [ ]         DGRAM                    12250    2056/goa-daemon     
unix  3      [ ]         STREAM     CONNECTED     12935    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12934    2051/mission-contro 
unix  3      [ ]         STREAM     CONNECTED     12933    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12241    2051/mission-contro 
unix  3      [ ]         STREAM     CONNECTED     12930    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12929    2051/mission-contro 
unix  3      [ ]         STREAM     CONNECTED     12236    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12235    2045/telepathy-indi 
unix  3      [ ]         STREAM     CONNECTED     12925    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12924    2045/telepathy-indi 
unix  3      [ ]         STREAM     CONNECTED     12233    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12232    2045/telepathy-indi 
unix  3      [ ]         STREAM     CONNECTED     12922    1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12231    2045/telepathy-indi 
unix  3      [ ]         STREAM     CONNECTED     12184    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12901    2041/gdu-notificati 
unix  3      [ ]         STREAM     CONNECTED     12900    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12183    2041/gdu-notificati 
unix  3      [ ]         STREAM     CONNECTED     12182    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12181    2041/gdu-notificati 
unix  3      [ ]         STREAM     CONNECTED     12898    1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12897    2041/gdu-notificati 
unix  3      [ ]         STREAM     CONNECTED     12887    1533/gnome-session  @/tmp/.ICE-unix/1533
unix  3      [ ]         STREAM     CONNECTED     12160    1821/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     12880    1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12135    1821/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     12688    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12684    2030/gtk-window-dec 
unix  3      [ ]         STREAM     CONNECTED     12682    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12678    2030/gtk-window-dec 
unix  3      [ ]         STREAM     CONNECTED     12679    1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12677    2030/gtk-window-dec 
unix  3      [ ]         STREAM     CONNECTED     12675    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12674    2028/ubuntu-geoip-p 
unix  3      [ ]         STREAM     CONNECTED     12671    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12670    2028/ubuntu-geoip-p 
unix  3      [ ]         STREAM     CONNECTED     12665    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11872    2021/geoclue-master 
unix  3      [ ]         STREAM     CONNECTED     12664    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11871    1983/indicator-date 
unix  3      [ ]         STREAM     CONNECTED     12663    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11870    1983/indicator-date 
unix  3      [ ]         STREAM     CONNECTED     12662    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12661    1976/indicator-prin 
unix  3      [ ]         STREAM     CONNECTED     12660    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12659    813/cupsd           
unix  3      [ ]         STREAM     CONNECTED     12658    813/cupsd           /var/run/cups/cups.sock
unix  3      [ ]         STREAM     CONNECTED     12657    1976/indicator-prin 
unix  3      [ ]         STREAM     CONNECTED     12656    1627/gnome-keyring- /tmp/keyring-psDKWR/pkcs11
unix  3      [ ]         STREAM     CONNECTED     12655    1976/indicator-prin 
unix  3      [ ]         STREAM     CONNECTED     11858    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12654    1977/indicator-soun 
unix  3      [ ]         STREAM     CONNECTED     11853    1821/pulseaudio     /home/george/.pulse/ca3e93814543fdce50702f190000000e-runtime/native
unix  3      [ ]         STREAM     CONNECTED     12651    1977/indicator-soun 
unix  3      [ ]         STREAM     CONNECTED     11857    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12646    2021/geoclue-master 
unix  3      [ ]         STREAM     CONNECTED     11850    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12644    1983/indicator-date 
unix  3      [ ]         STREAM     CONNECTED     11816    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11815    1976/indicator-prin 
unix  3      [ ]         STREAM     CONNECTED     12641    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12637    1983/indicator-date 
unix  3      [ ]         STREAM     CONNECTED     11806    1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11805    1976/indicator-prin 
unix  3      [ ]         STREAM     CONNECTED     12640    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11804    1983/indicator-date 
unix  3      [ ]         STREAM     CONNECTED     12639    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12629    1976/indicator-prin 
unix  3      [ ]         STREAM     CONNECTED     11782    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11779    1975/indicator-appl 
unix  3      [ ]         STREAM     CONNECTED     11781    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11778    1977/indicator-soun 
unix  3      [ ]         STREAM     CONNECTED     11780    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12620    1986/indicator-sess 
unix  3      [ ]         STREAM     CONNECTED     12621    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12619    1986/indicator-sess 
unix  3      [ ]         STREAM     CONNECTED     11777    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11776    1975/indicator-appl 
unix  3      [ ]         STREAM     CONNECTED     11773    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11772    1970/indicator-mess 
unix  3      [ ]         STREAM     CONNECTED     11771    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12613    1970/indicator-mess 
unix  3      [ ]         STREAM     CONNECTED     12600    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11768    1970/indicator-mess 
unix  3      [ ]         STREAM     CONNECTED     11770    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12599    1970/indicator-mess 
unix  3      [ ]         STREAM     CONNECTED     11745    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11744    1953/unity-panel-se 
unix  3      [ ]         STREAM     CONNECTED     11743    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11742    1953/unity-panel-se 
unix  3      [ ]         STREAM     CONNECTED     11741    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11740    1953/unity-panel-se 
unix  3      [ ]         STREAM     CONNECTED     11739    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12554    1953/unity-panel-se 
unix  3      [ ]         STREAM     CONNECTED     11736    1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     12553    1953/unity-panel-se 
unix  3      [ ]         STREAM     CONNECTED     12552    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12551    1954/hud-service    
unix  3      [ ]         STREAM     CONNECTED     12548    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12547    1954/hud-service    
unix  3      [ ]         STREAM     CONNECTED     12539    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12538    1807/compiz         
unix  3      [ ]         STREAM     CONNECTED     11709    1920/gvfsd-trash    @/dbus-vfs-daemon/socket-vbfNylbK
unix  3      [ ]         STREAM     CONNECTED     12537    1807/compiz         
unix  3      [ ]         STREAM     CONNECTED     11708    1920/gvfsd-trash    @/dbus-vfs-daemon/socket-hSyAkoOm
unix  3      [ ]         STREAM     CONNECTED     12536    1807/compiz         
unix  3      [ ]         STREAM     CONNECTED     11583    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11582    1946/bamfdaemon     
unix  3      [ ]         STREAM     CONNECTED     11579    1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11578    1946/bamfdaemon     
unix  3      [ ]         STREAM     CONNECTED     12501    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12500    1946/bamfdaemon     
unix  3      [ ]         STREAM     CONNECTED     12488    1920/gvfsd-trash    @/dbus-vfs-daemon/socket-90T5HRHc
unix  3      [ ]         STREAM     CONNECTED     12487    1807/compiz         
unix  3      [ ]         STREAM     CONNECTED     12486    1920/gvfsd-trash    @/dbus-vfs-daemon/socket-1bSKzkta
unix  3      [ ]         STREAM     CONNECTED     12485    1807/compiz         
unix  3      [ ]         STREAM     CONNECTED     12482    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12481    1807/compiz         
unix  3      [ ]         STREAM     CONNECTED     11567    1944/gvfsd-burn     @/dbus-vfs-daemon/socket-JYVpKvKl
unix  3      [ ]         STREAM     CONNECTED     12464    1834/nautilus       
unix  3      [ ]         STREAM     CONNECTED     11566    1944/gvfsd-burn     @/dbus-vfs-daemon/socket-43OsudUO
unix  3      [ ]         STREAM     CONNECTED     12463    1834/nautilus       
unix  3      [ ]         STREAM     CONNECTED     11560    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11559    1944/gvfsd-burn     
unix  3      [ ]         STREAM     CONNECTED     11544    1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11543    1807/compiz         
unix  3      [ ]         STREAM     CONNECTED     11542    1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11541    1807/compiz         
unix  3      [ ]         STREAM     CONNECTED     11540    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11539    1807/compiz         
unix  3      [ ]         STREAM     CONNECTED     12445    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12444    1631/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     12443    813/cupsd           /var/run/cups/cups.sock
unix  3      [ ]         STREAM     CONNECTED     12442    1804/colord         
unix  3      [ ]         STREAM     CONNECTED     12441    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12440    1804/colord         
unix  3      [ ]         STREAM     CONNECTED     12439    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12438    1804/colord         
unix  3      [ ]         STREAM     CONNECTED     12422    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12421    1807/compiz         
unix  3      [ ]         STREAM     CONNECTED     11525    1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11524    1807/compiz         
unix  3      [ ]         STREAM     CONNECTED     11518    1920/gvfsd-trash    @/dbus-vfs-daemon/socket-9mQGLQkf
unix  3      [ ]         STREAM     CONNECTED     12416    1834/nautilus       
unix  3      [ ]         STREAM     CONNECTED     11519    1920/gvfsd-trash    @/dbus-vfs-daemon/socket-RxqYe13u
unix  3      [ ]         STREAM     CONNECTED     12415    1834/nautilus       
unix  3      [ ]         STREAM     CONNECTED     12392    1920/gvfsd-trash    @/dbus-vfs-daemon/socket-qDXJa1Zr
unix  3      [ ]         STREAM     CONNECTED     12391    1834/nautilus       
unix  3      [ ]         STREAM     CONNECTED     12393    1920/gvfsd-trash    @/dbus-vfs-daemon/socket-vbAjRE8u
unix  3      [ ]         STREAM     CONNECTED     12390    1834/nautilus       
unix  3      [ ]         STREAM     CONNECTED     12379    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11427    1839/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     12375    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12374    1920/gvfsd-trash    
unix  3      [ ]         STREAM     CONNECTED     12358    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12357    1920/gvfsd-trash    
unix  3      [ ]         STREAM     CONNECTED     11414    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11413    1834/nautilus       
unix  3      [ ]         STREAM     CONNECTED     12301    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11354    1834/nautilus       
unix  3      [ ]         STREAM     CONNECTED     12300    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12299    1839/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     12298    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11348    1839/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     12292    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     12291    1834/nautilus       
unix  2      [ ]         DGRAM                    12290    803/polkitd         
unix  2      [ ]         DGRAM                    11264    1863/dnsmasq        
unix  3      [ ]         STREAM     CONNECTED     11223    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11222    1835/polkit-gnome-a 
unix  3      [ ]         STREAM     CONNECTED     11221    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11220    1837/bluetooth-appl 
unix  3      [ ]         STREAM     CONNECTED     11312    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11311    1860/gvfs-afc-volum 
unix  3      [ ]         STREAM     CONNECTED     11304    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11303    1858/gvfs-gphoto2-v 
unix  3      [ ]         STREAM     CONNECTED     11297    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11296    1851/gvfs-gdu-volum 
unix  3      [ ]         STREAM     CONNECTED     11293    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11292    1853/udisks-daemon  
unix  3      [ ]         STREAM     CONNECTED     11289    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11288    1853/udisks-daemon  
unix  3      [ ]         STREAM     CONNECTED     11278    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11212    1851/gvfs-gdu-volum 
unix  3      [ ]         STREAM     CONNECTED     11206    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11205    1851/gvfs-gdu-volum 
unix  3      [ ]         STREAM     CONNECTED     11276    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11275    1833/gnome-fallback 
unix  3      [ ]         STREAM     CONNECTED     11201    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11200    1833/gnome-fallback 
unix  3      [ ]         STREAM     CONNECTED     11199    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11198    1834/nautilus       
unix  3      [ ]         STREAM     CONNECTED     11197    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11196    1839/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     11195    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11194    1837/bluetooth-appl 
unix  3      [ ]         STREAM     CONNECTED     11193    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11192    1835/polkit-gnome-a 
unix  3      [ ]         STREAM     CONNECTED     11181    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11272    1839/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     11190    1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11271    1839/nm-applet      
unix  3      [ ]         STREAM     CONNECTED     11189    1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11178    1837/bluetooth-appl 
unix  3      [ ]         STREAM     CONNECTED     11177    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11176    1837/bluetooth-appl 
unix  3      [ ]         STREAM     CONNECTED     11174    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11268    1835/polkit-gnome-a 
unix  3      [ ]         STREAM     CONNECTED     11188    1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11267    1835/polkit-gnome-a 
unix  3      [ ]         STREAM     CONNECTED     11187    1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11173    1834/nautilus       
unix  3      [ ]         STREAM     CONNECTED     11172    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11266    1834/nautilus       
unix  3      [ ]         STREAM     CONNECTED     11148    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     10237    1833/gnome-fallback 
unix  3      [ ]         STREAM     CONNECTED     11127    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11126    1833/gnome-fallback 
unix  3      [ ]         STREAM     CONNECTED     10233    1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11106    1833/gnome-fallback 
unix  3      [ ]         STREAM     CONNECTED     10209    1533/gnome-session  @/tmp/.ICE-unix/1533
unix  3      [ ]         STREAM     CONNECTED     11063    1807/compiz         
unix  3      [ ]         STREAM     CONNECTED     10207    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     10206    1631/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     11062    1821/pulseaudio     /home/george/.pulse/ca3e93814543fdce50702f190000000e-runtime/native
unix  3      [ ]         STREAM     CONNECTED     10205    1631/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     11060    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     10204    1831/gconf-helper   
unix  3      [ ]         STREAM     CONNECTED     11023    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10198    1821/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     10190    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     10189    1828/gvfsd-metadata 
unix  3      [ ]         STREAM     CONNECTED     11013    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     11012    1807/compiz         
unix  3      [ ]         STREAM     CONNECTED     11010    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     10186    1821/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     10999    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10998    1823/rtkit-daemon   
unix  2      [ ]         DGRAM                    10997    1823/rtkit-daemon   
unix  3      [ ]         STREAM     CONNECTED     10989    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10171    1821/pulseaudio     
unix  3      [ ]         STREAM     CONNECTED     10981    1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10143    1816/syndaemon      
unix  3      [ ]         STREAM     CONNECTED     10958    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10957    1810/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     10124    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     10123    1810/gconfd-2       
unix  3      [ ]         STREAM     CONNECTED     10945    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     10944    1807/compiz         
unix  3      [ ]         STREAM     CONNECTED     10941    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     10119    1807/compiz         
unix  3      [ ]         STREAM     CONNECTED     10939    1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10938    1807/compiz         
unix  3      [ ]         STREAM     CONNECTED     10049    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10918    1804/colord         
unix  3      [ ]         STREAM     CONNECTED     10910    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     10909    1533/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     10882    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     10881    1716/gvfs-fuse-daem 
unix  3      [ ]         STREAM     CONNECTED     10879    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     10878    1716/gvfs-fuse-daem 
unix  3      [ ]         STREAM     CONNECTED     10856    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     10855    1707/gvfsd          
unix  3      [ ]         STREAM     CONNECTED     9965     1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     10851    1631/gnome-settings 
unix  2      [ ]         DGRAM                    10803    1658/dhclient       
unix  3      [ ]         STREAM     CONNECTED     10751    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9893     1639/upowerd        
unix  3      [ ]         STREAM     CONNECTED     9890     710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10750    1639/upowerd        
unix  3      [ ]         STREAM     CONNECTED     9882     710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10748    1631/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     9881     710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9880     1631/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     10745    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     9879     1631/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     9877     1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9876     1631/gnome-settings 
unix  3      [ ]         STREAM     CONNECTED     10734    1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     9873     1627/gnome-keyring- 
unix  3      [ ]         STREAM     CONNECTED     9865     1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     9864     1627/gnome-keyring- 
unix  3      [ ]         STREAM     CONNECTED     9860     1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     10598    1533/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     9859     1619/dbus-daemon    @/tmp/dbus-9pFOfqQd4T
unix  3      [ ]         STREAM     CONNECTED     9858     1533/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     10597    1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10596    1533/gnome-session  
unix  3      [ ]         STREAM     CONNECTED     9855     1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     9854     1618/dbus-launch    
unix  3      [ ]         STREAM     CONNECTED     10593    1619/dbus-daemon    
unix  3      [ ]         STREAM     CONNECTED     10592    1619/dbus-daemon    
unix  3      [ ]         STREAM     CONNECTED     9846     1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10586    1618/dbus-launch    
unix  3      [ ]         STREAM     CONNECTED     9664     710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9663     1444/console-kit-da 
unix  3      [ ]         STREAM     CONNECTED     9657     710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9656     1444/console-kit-da 
unix  2      [ ]         DGRAM                    9649     1384/lightdm        
unix  3      [ ]         STREAM     CONNECTED     9590     710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10370    1387/accounts-daemo 
unix  3      [ ]         STREAM     CONNECTED     9587     710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10369    1387/accounts-daemo 
unix  3      [ ]         STREAM     CONNECTED     9579     710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     10365    1384/lightdm        
unix  3      [ ]         STREAM     CONNECTED     9556     1370/X              @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     10360    1336/lightdm        
unix  3      [ ]         STREAM     CONNECTED     10338    1122/acpid          /var/run/acpid.socket
unix  3      [ ]         STREAM     CONNECTED     9533     1370/X              
unix  3      [ ]         STREAM     CONNECTED     10313    710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9510     1336/lightdm        
unix  3      [ ]         STREAM     CONNECTED     9329     710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9328     1119/whoopsie       
unix  2      [ ]         DGRAM                    8548     1122/acpid          
unix  2      [ ]         DGRAM                    8547     1121/anacron        
unix  3      [ ]         STREAM     CONNECTED     8192     710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8191     982/wpa_supplicant  
unix  2      [ ]         DGRAM                    8190     982/wpa_supplicant  
unix  3      [ ]         STREAM     CONNECTED     8097     1/init              @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     8091     931/upstart-socket- 
unix  3      [ ]         STREAM     CONNECTED     8202     710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8022     821/avahi-daemon: r 
unix  3      [ ]         STREAM     CONNECTED     8017     823/avahi-daemon: c 
unix  3      [ ]         STREAM     CONNECTED     8016     821/avahi-daemon: r 
unix  2      [ ]         DGRAM                    8014     821/avahi-daemon: r 
unix  2      [ ]         DGRAM                    8200     792/NetworkManager  
unix  2      [ ]         DGRAM                    8197     710/dbus-daemon     
unix  3      [ ]         STREAM     CONNECTED     7156     710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7155     803/polkitd         
unix  3      [ ]         STREAM     CONNECTED     7145     710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7144     792/NetworkManager  
unix  3      [ ]         STREAM     CONNECTED     7139     710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7138     792/NetworkManager  
unix  3      [ ]         STREAM     CONNECTED     7826     710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7825     744/bluetoothd      
unix  3      [ ]         STREAM     CONNECTED     7814     710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7813     742/modem-manager   
unix  3      [ ]         STREAM     CONNECTED     7807     710/dbus-daemon     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     7806     1/init              
unix  3      [ ]         STREAM     CONNECTED     7771     710/dbus-daemon     
unix  3      [ ]         STREAM     CONNECTED     7770     710/dbus-daemon     
unix  3      [ ]         DGRAM                    6454     375/udevd           
unix  3      [ ]         DGRAM                    6453     375/udevd           
unix  3      [ ]         STREAM     CONNECTED     6410     1/init              @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     6407     363/upstart-udev-br 
george@george-Satellite-A215:~$

---

### Post by geomcd1949 on 2012-05-09
> **kellemes said:**
> Apache is running?
```
sudo /etc/init.d/apache2 restart
```


george@george-Satellite-A215:~$ sudo /etc/init.d/apache2 restart
[sudo] password for george: 
Syntax error on line 1 of /etc/apache2/conf.d/fqdn:
Invalid command 'Server', perhaps misspelled or defined by a module not included in the server configuration
Action 'configtest' failed.
The Apache error log may have more information.
   ...fail!
george@george-Satellite-A215:~$

---

