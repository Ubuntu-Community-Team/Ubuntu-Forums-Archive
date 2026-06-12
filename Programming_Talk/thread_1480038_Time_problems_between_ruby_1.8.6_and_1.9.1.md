---
title: "Time problems between ruby 1.8.6 and 1.9.1"
date: 2010-05-11
forum: Programming Talk
---

### Post by firekilroy on 2010-05-11
Hello,
I wrote a ruby-script that used Time on a machine with v1.9.1. When I
now try to use it on a machine with v1.8.6, the Time-part is acting up.
It looks to me like the strftime-option gets ignored totally in 1.8.6.
It should give me todays date + the number of the last hour ie
'2010-05-11 13', if the time was 14:27 when the script ran, but it gives
me either 'Tue May 11 ...' or 'Thu Jan 01 ... 1970'. On the 1.9.1 system
it worked just fine, but it has never worked on the 1.8.6 system.

Was there a major rewrite of Time between 1.8.6 and 1.9.1 or is my
script just plain wrong?

```
#!/usr/bin/ruby -w
    require 'rubygems'
    require 'mysql'
    require 'ipaddr'
    require 'socket'
    require 'time'

begin
        t = Time.now.strftime("%Y-%m-%d %H").to_i
#       t = Time.now
        print t.to_s + "\n"
        t2 = t.to_i - 3600
        t2 = Time.at(t2)
        print t2.to_s + "\n"
        t3 = t2.to_s.slice! 0..12
        print t3.to_s + "\n"

    dbh = Mysql.real_connect("10.199.198.4", "root", "cisco", "snorbydb")
        res = dbh.query("select event.timestamp, event.cid from event join signature on event.signature = signature.sig_id where signature.sig_priority < 3 order by event.cid;\n")
    dbh.close
    index = 0
    row_id = []
    collect = []
    fil = File.open("filter_cid.txt", "w")
    while row_id = res.fetch_row do
        fil.puts row_id[0] + "<" + row_id[1]
        index +=1
    end
    t3full = t3
    t3a = t3full.slice! 0..3
    t3b = t3full.slice! 1..2
    t3c = t3full.slice! 2..3
    t3d = t3full.slice! 3..4
    t4 = "cat filter_cid.txt | grep \"#{t3a}-#{t3b}-#{t3c} #{t3d}\" | cut -d'<' -f2 > klara_cid.txt"
    system("sh snorbycid.sh #{t3a} #{t3b} #{t3c} #{t3d}")
    fil.close
    
    cid = []
    fil = File.open("klara_cid.txt", "r")
    fil.each_line{ |line| cid << line.chomp}
    fil.close
    
    index=0
    while index < cid.length do
        print "C"
        index +=1
    end

    if cid.length < 1 then
        exit
    else
    
        index = 0
        row_cid = []
        ip = []
        prio = []
        dbh = Mysql.real_connect("10.199.198.4", "root", "cisco", "snorbydb")
        while index < cid.length do
            res = dbh.query("SELECT iphdr.ip_src, signature.sig_priority from iphdr join (event join signature on event.signature = signature.sig_id) on event.cid = iphdr.cid where event.cid = #{cid[index]};\n")
            while row_cid = res.fetch_row do
                ip[index] = row_cid[0]
                prio[index] = row_cid[1]
            end
            print "P"
            index +=1
        end

        dbh.close
        
        index = 0
        ip_filter = []
        while index < ip.length do    
            ip_filter[index] = IPAddr.new(Integer(ip[index]), Socket::AF_INET).to_s
            index +=1
        end
        
        index = 0
        tm = []
        while index < prio.length do
            if prio[index] == "2" then
                tm[index] = 5
            elsif prio[index] == "1" then
                tm[index] = 8
            else
                tm[index] = 0
            end
            index +=1
        end
    
        index = 0
        dbh = Mysql.real_connect("10.199.198.5", "root", "cisco", "hostlist")
        while index < tm.length do
            if tm[index] == 5 then
            dbh.query("update Hosts set `TM-Sn`=#{tm[index]} where IP='#{ip_filter[index]}';\n")
            end
            print "M"
            index +=1
        end
        index = 0
        while index < tm.length do
                        if tm[index] == 8 then
                        dbh.query("update Hosts set `TM-Sn`=#{tm[index]} where IP='#{ip_filter[index]}';\n")
                        end
            print "H"
                        index +=1
                end
        dbh.close
        print "\n"
    end
end


```

---

### Post by firekilroy on 2010-05-11
SOLVED, see [http://www.ruby-forum.com/topic/209575#911406](http://www.ruby-forum.com/topic/209575#911406)

---

