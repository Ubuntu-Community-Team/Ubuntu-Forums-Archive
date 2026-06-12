---
title: "How to keep data each 1 minute?(looping)"
date: 2013-05-09
forum: Programming Talk
---

### Post by Newbie89 on 2013-05-09
How do I keep data for each 1 minute?I think insert query first and then delete each times.Can some help me check and recorrect my code?

> 
 if (T_Time >= InTime) 
      {  
          if (cal_count<60)
      {
     printf("insert data till one minute\n");                    
     sprintf(sql_lite, "insert into Packet (Dated,Time,Src_MAC,Dest_MAC,Net_P,Trans_P,Src_IP,Dest_IP,Src_Port,Dest_Port,Cap_Bytes) values ('%s','%s','%s','%s','%s','%s','%s','%s','%ld','%ld','%ld');",DT, TM, Src_MAC, Dest_MAC, Net_P,Trans_P, Src_IP, Dest_IP, Src_Port, Dest_Port, Cap_Bytes); 
    error = sqlite3_exec(conn, sql_lite, 0, 0, 0);
    cal_count=cal_count+1; 
      }
     else 
       {        
       printf("update each one minute\n");
       sprintf(del_lite,"delete from Packet;");
       error = sqlite3_exec(conn, del_lite, 0, 0, 0);               
         /*printf("Date=%s\tTime=%s\nSrc_MAC=%s\tDest MAC=%s\nNet_P=%s\tTrans_P=%s\nSrc_IP=%s\tDest_IP=%s\nSrc_Port=%ld\tDest_Port=%ld\nPacket Size=%ld\n", DT, TM, Src_MAC, Dest_MAC, Net_P,Trans_P, Src_IP, Dest_IP, Src_Port, Dest_Port, Cap_Bytes);*/  
          sleep(1);
      } 
      } 
      else  
        break; 


I try and found that something wrong in my code.In my code just for one minute to keep data.How do I keep data for each 1 minute?

---

### Post by azzamite on 2013-05-09
Not sure I understood, but I you could try moving the sleep(1); outside the if
so that both paths will introduce a delay.

---

### Post by Newbie89 on 2013-05-10
> **azzamite said:**
> Not sure I understood, but I you could try moving the sleep(1); outside the if
so that both paths will introduce a delay.

I have moving the sleep(1); outside the if loop.I want it to perform continuously like keep data for 1 minute,then delete it and insert again for another 1 minute.Repeatably.

---

