---
title: "is this a normal netstat?"
date: 2013-09-28
forum: New to Ubuntu
---

### Post by jwkramlinger on 2013-09-28
hi.  a computer im using is seeming unusually slow today so I did a netstat and this is the output.   The problem is, I'm really not sure what most of it is.  Seems like a lot of connections for a personal computer?


```
Proto RefCnt Flags       Type       State         I-Node   Path
unix  15     [ ]         DGRAM                    2351     /dev/log
unix  2      [ ]         DGRAM                    13666    
unix  3      [ ]         SEQPACKET  CONNECTED     11374798 
unix  3      [ ]         STREAM     CONNECTED     269667   
unix  3      [ ]         STREAM     CONNECTED     149738   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     11863016 
unix  3      [ ]         STREAM     CONNECTED     94014    @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     166193   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     151768   
unix  3      [ ]         STREAM     CONNECTED     149679   
unix  3      [ ]         STREAM     CONNECTED     11374790 
unix  3      [ ]         STREAM     CONNECTED     151868   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     93881    
unix  3      [ ]         STREAM     CONNECTED     151034   
unix  3      [ ]         STREAM     CONNECTED     151729   
unix  3      [ ]         STREAM     CONNECTED     152029   
unix  2      [ ]         DGRAM                    1446     
unix  3      [ ]         STREAM     CONNECTED     100498   
unix  3      [ ]         STREAM     CONNECTED     90584    @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     2208330  @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     266419   
unix  3      [ ]         STREAM     CONNECTED     1473     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     90575    @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     14943466 @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     90605    @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         SEQPACKET  CONNECTED     11866127 
unix  3      [ ]         STREAM     CONNECTED     9892     @/tmp/.X11-unix/X0
unix  2      [ ]         DGRAM                    9830     
unix  3      [ ]         STREAM     CONNECTED     151736   
unix  3      [ ]         STREAM     CONNECTED     94039    @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     101774   
unix  3      [ ]         STREAM     CONNECTED     94035    @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     11374875 
unix  3      [ ]         STREAM     CONNECTED     267896   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     151845   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     2241666  
unix  3      [ ]         STREAM     CONNECTED     149773   
unix  3      [ ]         STREAM     CONNECTED     11329418 @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     93915    
unix  3      [ ]         STREAM     CONNECTED     8575     @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     11392315 
unix  3      [ ]         STREAM     CONNECTED     155305   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     101788   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     151263   
unix  3      [ ]         STREAM     CONNECTED     151844   
unix  3      [ ]         STREAM     CONNECTED     11391334 
unix  3      [ ]         STREAM     CONNECTED     150879   
unix  3      [ ]         STREAM     CONNECTED     90549    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     270477   
unix  3      [ ]         STREAM     CONNECTED     151822   
unix  3      [ ]         STREAM     CONNECTED     100619   
unix  3      [ ]         STREAM     CONNECTED     150684   
unix  3      [ ]         STREAM     CONNECTED     23300    
unix  3      [ ]         STREAM     CONNECTED     150318   
unix  3      [ ]         STREAM     CONNECTED     149836   @/dbus-vfs-daemon/socket-EjDD7iPS
unix  3      [ ]         STREAM     CONNECTED     153442   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11868561 @/tmp/dbus-6vmckQ89Ml
unix  3      [ ]         STREAM     CONNECTED     11869422 @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     151847   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11859559 
unix  3      [ ]         STREAM     CONNECTED     151260   
unix  3      [ ]         STREAM     CONNECTED     149664   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     149761   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     12519    @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     23392    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     8961     @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     11374794 
unix  3      [ ]         STREAM     CONNECTED     23491    
unix  3      [ ]         STREAM     CONNECTED     101781   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     101742   
unix  3      [ ]         STREAM     CONNECTED     13656    
unix  3      [ ]         STREAM     CONNECTED     11865864 
unix  2      [ ]         DGRAM                    2235092  
unix  3      [ ]         STREAM     CONNECTED     150880   
unix  3      [ ]         STREAM     CONNECTED     151741   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     157939   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     101786   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     90465    
unix  3      [ ]         STREAM     CONNECTED     11388857 
unix  3      [ ]         STREAM     CONNECTED     11392214 
unix  3      [ ]         STREAM     CONNECTED     150125   
unix  2      [ ]         DGRAM                    23484    
unix  3      [ ]         STREAM     CONNECTED     90518    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11868562 
unix  3      [ ]         STREAM     CONNECTED     90576    
unix  3      [ ]         STREAM     CONNECTED     151733   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     94043    @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         SEQPACKET  CONNECTED     11841362 
unix  3      [ ]         STREAM     CONNECTED     11863018 
unix  2      [ ]         DGRAM                    9028     
unix  3      [ ]         SEQPACKET  CONNECTED     11385987 
unix  3      [ ]         STREAM     CONNECTED     94019    
unix  3      [ ]         STREAM     CONNECTED     11394219 
unix  3      [ ]         STREAM     CONNECTED     11391328 
unix  3      [ ]         STREAM     CONNECTED     2199513  
unix  3      [ ]         STREAM     CONNECTED     157935   
unix  3      [ ]         STREAM     CONNECTED     1447     
unix  3      [ ]         STREAM     CONNECTED     93916    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     13669    
unix  3      [ ]         STREAM     CONNECTED     90732    @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     90589    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14827209 
unix  2      [ ]         DGRAM                    10077761 
unix  3      [ ]         STREAM     CONNECTED     151896   
unix  3      [ ]         STREAM     CONNECTED     100505   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     11863015 
unix  3      [ ]         STREAM     CONNECTED     150725   
unix  3      [ ]         STREAM     CONNECTED     90730    
unix  2      [ ]         DGRAM                    11385989 
unix  3      [ ]         STREAM     CONNECTED     149809   
unix  3      [ ]         STREAM     CONNECTED     23483    
unix  3      [ ]         STREAM     CONNECTED     11389856 
unix  3      [ ]         STREAM     CONNECTED     160412   
unix  3      [ ]         STREAM     CONNECTED     90593    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11329417 /run/user/jwk/pulse/native
unix  3      [ ]         STREAM     CONNECTED     90729    
unix  3      [ ]         STREAM     CONNECTED     9085     
unix  3      [ ]         STREAM     CONNECTED     2368     
unix  3      [ ]         STREAM     CONNECTED     12125884 
unix  3      [ ]         STREAM     CONNECTED     93880    @/tmp/dbus-6vmckQ89Ml
unix  3      [ ]         STREAM     CONNECTED     11388772 
unix  3      [ ]         STREAM     CONNECTED     153448   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     149697   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     149671   /var/run/dbus/system_bus_socket
unix  3      [ ]         SEQPACKET  CONNECTED     11385984 
unix  3      [ ]         STREAM     CONNECTED     151979   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     23405    
unix  3      [ ]         STREAM     CONNECTED     151821   
unix  3      [ ]         STREAM     CONNECTED     93973    
unix  3      [ ]         STREAM     CONNECTED     151911   
unix  3      [ ]         SEQPACKET  CONNECTED     11866126 
unix  3      [ ]         STREAM     CONNECTED     13513    
unix  2      [ ]         DGRAM                    163769   
unix  3      [ ]         STREAM     CONNECTED     151850   
unix  3      [ ]         STREAM     CONNECTED     151742   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     149687   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     1576     
unix  3      [ ]         STREAM     CONNECTED     1545287  /var/run/acpid.socket
unix  2      [ ]         DGRAM                    14879972 
unix  3      [ ]         STREAM     CONNECTED     90562    
unix  3      [ ]         STREAM     CONNECTED     150127   /run/user/jwk/pulse/native
unix  3      [ ]         STREAM     CONNECTED     90594    
unix  3      [ ]         STREAM     CONNECTED     90573    
unix  3      [ ]         STREAM     CONNECTED     93990    
unix  3      [ ]         STREAM     CONNECTED     149784   
unix  3      [ ]         STREAM     CONNECTED     23306    @/tmp/.X11-unix/X0
unix  2      [ ]         DGRAM                    2235096  
unix  3      [ ]         STREAM     CONNECTED     153645   
unix  3      [ ]         STREAM     CONNECTED     153431   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     149785   @/tmp/dbus-wUQquLYvbh
unix  2      [ ]         DGRAM                    151837   
unix  2      [ ]         DGRAM                    162178   
unix  3      [ ]         STREAM     CONNECTED     152024   
unix  3      [ ]         STREAM     CONNECTED     11391369 
unix  3      [ ]         STREAM     CONNECTED     10537    
unix  3      [ ]         STREAM     CONNECTED     155310   
unix  3      [ ]         STREAM     CONNECTED     1343     
unix  3      [ ]         STREAM     CONNECTED     149755   @/tmp/dbus-6vmckQ89Ml
unix  3      [ ]         STREAM     CONNECTED     11864711 
unix  3      [ ]         STREAM     CONNECTED     151856   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     90731    @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     93995    
unix  3      [ ]         STREAM     CONNECTED     149758   /run/user/jwk/pulse/native
unix  3      [ ]         STREAM     CONNECTED     12662    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     149680   
unix  3      [ ]         STREAM     CONNECTED     11869423 @/tmp/.ICE-unix/4982
unix  3      [ ]         STREAM     CONNECTED     11834886 
unix  3      [ ]         STREAM     CONNECTED     11859558 
unix  3      [ ]         STREAM     CONNECTED     100501   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     151728   
unix  3      [ ]         STREAM     CONNECTED     149749   @/tmp/dbus-wUQquLYvbh
unix  2      [ ]         DGRAM                    11426158 
unix  3      [ ]         STREAM     CONNECTED     101783   
unix  3      [ ]         STREAM     CONNECTED     12665    /var/run/dbus/system_bus_socket
unix  3      [ ]         SEQPACKET  CONNECTED     11374799 
unix  3      [ ]         STREAM     CONNECTED     11392280 
unix  3      [ ]         STREAM     CONNECTED     151769   
unix  3      [ ]         STREAM     CONNECTED     1470     /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11374788 
unix  3      [ ]         STREAM     CONNECTED     2481     
unix  3      [ ]         STREAM     CONNECTED     149760   
unix  3      [ ]         STREAM     CONNECTED     149678   
unix  3      [ ]         STREAM     CONNECTED     11391370 
unix  3      [ ]         STREAM     CONNECTED     94023    @/tmp/dbus-6vmckQ89Ml
unix  3      [ ]         STREAM     CONNECTED     149776   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     14879966 
unix  3      [ ]         STREAM     CONNECTED     100802   @/tmp/dbus-6vmckQ89Ml
unix  3      [ ]         STREAM     CONNECTED     94055    @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         DGRAM                    11444    
unix  3      [ ]         STREAM     CONNECTED     12152850 @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     11392281 
unix  3      [ ]         STREAM     CONNECTED     94015    @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     268101   
unix  3      [ ]         STREAM     CONNECTED     151731   
unix  3      [ ]         STREAM     CONNECTED     8564     @/com/ubuntu/upstart
unix  3      [ ]         STREAM     CONNECTED     11374791 
unix  3      [ ]         STREAM     CONNECTED     101663   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     151857   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     149699   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     11388773 
unix  3      [ ]         SEQPACKET  CONNECTED     11385985 
unix  3      [ ]         STREAM     CONNECTED     11391333 
unix  3      [ ]         STREAM     CONNECTED     2240861  @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     2239670  
unix  3      [ ]         STREAM     CONNECTED     12668    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     9808     
unix  3      [ ]         STREAM     CONNECTED     94063    @/dbus-vfs-daemon/socket-qQTipqZc
unix  3      [ ]         STREAM     CONNECTED     150304   
unix  3      [ ]         STREAM     CONNECTED     14820054 @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     90623    @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     90470    
unix  3      [ ]         STREAM     CONNECTED     149759   @/tmp/dbus-6vmckQ89Ml
unix  3      [ ]         STREAM     CONNECTED     11388748 @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     150881   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     11391604 /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     2240558  @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     90539    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     149772   
unix  3      [ ]         STREAM     CONNECTED     269564   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     90563    
unix  2      [ ]         DGRAM                    14879976 
unix  3      [ ]         STREAM     CONNECTED     152813   
unix  3      [ ]         STREAM     CONNECTED     163777   
unix  3      [ ]         STREAM     CONNECTED     1426     
unix  3      [ ]         STREAM     CONNECTED     90451    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     1549396  
unix  3      [ ]         STREAM     CONNECTED     151851   
unix  3      [ ]         STREAM     CONNECTED     1577     
unix  3      [ ]         STREAM     CONNECTED     150688   
unix  3      [ ]         STREAM     CONNECTED     100739   
unix  3      [ ]         STREAM     CONNECTED     101662   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     151975   
unix  3      [ ]         STREAM     CONNECTED     2240555  @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     11374787 
unix  3      [ ]         STREAM     CONNECTED     23385    
unix  3      [ ]         STREAM     CONNECTED     157943   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     90560    @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     90466    
unix  3      [ ]         STREAM     CONNECTED     151259   
unix  3      [ ]         STREAM     CONNECTED     11863400 @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     90460    
unix  3      [ ]         STREAM     CONNECTED     11864568 
unix  3      [ ]         STREAM     CONNECTED     151261   
unix  3      [ ]         STREAM     CONNECTED     151029   @/tmp/dbus-6vmckQ89Ml
unix  3      [ ]         STREAM     CONNECTED     267869   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     151767   
unix  3      [ ]         STREAM     CONNECTED     100737   
unix  3      [ ]         STREAM     CONNECTED     11834885 
unix  3      [ ]         STREAM     CONNECTED     2199512  
unix  3      [ ]         STREAM     CONNECTED     90546    @/tmp/.ICE-unix/4982
unix  3      [ ]         STREAM     CONNECTED     2241599  
unix  3      [ ]         STREAM     CONNECTED     93882    
unix  3      [ ]         STREAM     CONNECTED     153443   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     94029    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     101741   
unix  3      [ ]         STREAM     CONNECTED     101780   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11388858 
unix  3      [ ]         STREAM     CONNECTED     93871    @/tmp/.X11-unix/X0
unix  3      [ ]         DGRAM                    11443    
unix  3      [ ]         STREAM     CONNECTED     101765   
unix  3      [ ]         STREAM     CONNECTED     13506    
unix  3      [ ]         STREAM     CONNECTED     153455   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     90522    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     90461    @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     90577    
unix  3      [ ]         STREAM     CONNECTED     151737   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     9932     @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     94001    @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     94021    
unix  3      [ ]         STREAM     CONNECTED     11869424 @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     23305    @/tmp/dbus-6vmckQ89Ml
unix  3      [ ]         STREAM     CONNECTED     100499   
unix  3      [ ]         STREAM     CONNECTED     151895   
unix  3      [ ]         STREAM     CONNECTED     149748   
unix  3      [ ]         STREAM     CONNECTED     23382    
unix  3      [ ]         STREAM     CONNECTED     151879   
unix  3      [ ]         STREAM     CONNECTED     13672    
unix  3      [ ]         STREAM     CONNECTED     11865863 
unix  3      [ ]         STREAM     CONNECTED     11389868 @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     150859   
unix  3      [ ]         STREAM     CONNECTED     153643   
unix  3      [ ]         STREAM     CONNECTED     270677   @/tmp/.ICE-unix/4982
unix  3      [ ]         STREAM     CONNECTED     150730   
unix  3      [ ]         STREAM     CONNECTED     1427     /var/run/dbus/system_bus_socket
unix  3      [ ]         SEQPACKET  CONNECTED     11385988 
unix  3      [ ]         STREAM     CONNECTED     151734   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     11391329 
unix  3      [ ]         STREAM     CONNECTED     90587    
unix  3      [ ]         STREAM     CONNECTED     93919    
unix  3      [ ]         STREAM     CONNECTED     149754   /run/user/jwk/pulse/native
unix  3      [ ]         STREAM     CONNECTED     150713   
unix  3      [ ]         STREAM     CONNECTED     90552    
unix  3      [ ]         STREAM     CONNECTED     23398    
unix  3      [ ]         STREAM     CONNECTED     11864569 
unix  3      [ ]         STREAM     CONNECTED     151028   @/tmp/dbus-6vmckQ89Ml
unix  3      [ ]         STREAM     CONNECTED     100618   @/tmp/.X11-unix/X0
unix  3      [ ]         STREAM     CONNECTED     101787   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     151732   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     93989    
unix  3      [ ]         STREAM     CONNECTED     149668   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     93951    /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     11374793 
unix  3      [ ]         STREAM     CONNECTED     150319   
unix  3      [ ]         STREAM     CONNECTED     23299    
unix  3      [ ]         STREAM     CONNECTED     1425     
unix  3      [ ]         STREAM     CONNECTED     11374874 
unix  3      [ ]         STREAM     CONNECTED     94046    @/tmp/dbus-wUQquLYvbh
unix  2      [ ]         STREAM     CONNECTED     1575     
unix  3      [ ]         STREAM     CONNECTED     151978   
unix  3      [ ]         STREAM     CONNECTED     163778   
unix  3      [ ]         STREAM     CONNECTED     155311   
unix  3      [ ]         STREAM     CONNECTED     151698   
unix  2      [ ]         DGRAM                    13653    
unix  3      [ ]         SEQPACKET  CONNECTED     11841361 
unix  3      [ ]         STREAM     CONNECTED     100803   @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     152810   
unix  3      [ ]         STREAM     CONNECTED     151848   @/tmp/.ICE-unix/4982
unix  3      [ ]         STREAM     CONNECTED     2238122  @/tmp/dbus-wUQquLYvbh
unix  3      [ ]         STREAM     CONNECTED     11392314 
unix  3      [ ]         STREAM     CONNECTED     90574    
unix  3      [ ]         STREAM     CONNECTED     149775   /var/run/dbus/system_bus_socket
unix  3      [ ]         STREAM     CONNECTED     23301    @/tmp/dbus-6vmckQ89Ml
unix  3      [ ]         STREAM     CONNECTED     101782   
unix  3      [ ]         STREAM     CONNECTED     94000    @/tmp/.X11-unix/X0
```

---

### Post by tgalati4 on 2013-09-28
That's normal.  Install htop and report what you see.

Open a terminal:

```
sudo apt-get install htop
htop
```

---

