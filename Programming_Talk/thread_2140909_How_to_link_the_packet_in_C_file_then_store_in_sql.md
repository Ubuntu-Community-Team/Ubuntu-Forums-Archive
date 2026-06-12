---
title: "How to link the packet in C file then store in sqlite database?"
date: 2013-05-01
forum: Programming Talk
---

### Post by Newbie89 on 2013-05-01
Here is the code I need to focus:


> struct Packet 
{ 
   char Src_MAC[18], Dest_MAC[18]; 
   char Net_P[5],Trans_P[5];  
   char Src_IP[16], Dest_IP[16];          
   long int Src_Port,Dest_Port, Cap_Bytes;    //[ long int Range: &#8722;2,147,483,648 to 2,147,483,647] 
}; 

struct Packet Pack[60000];        
 
void ProcessPack(u_char *ul,const struct pcap_pkthdr* pkthdr,const u_char*pckt) 
{      
  // Declare pointers to packet headers  
  const struct sniff_ip *ip;              // IP Header Pointer  
  const struct sniff_tcp *tcp;            // TCP Header Pointer  
  const struct sniff_udp *udp;            // TCP Header Pointer 
  struct sniff_ethernet *eptr;            // Ethernet Header Pointer  
 
  int size_ip; 
  int size_tcp; 
  char buffer[65535]; 
  
  // Capture packet length in Bytes 
  Pack[Cnt].Cap_Bytes = pkthdr->len; 
  TB += pkthdr->len; 
 
//================ Ethernet Header Info ============================== 
 
   eptr = (struct sniff_ethernet*)(pckt); 
 
   ip = (struct sniff_ip*) (pckt + SIZE_ETHERNET); 
   size_ip = IP_HL(ip)*4;   
 
   tcp = (struct sniff_tcp*) (pckt + SIZE_ETHERNET + size_ip); 
   size_tcp = TH_OFF(tcp)*4; 
   
   if ( (size_ip < 20) || (size_tcp < 20))  
   { 
      
     if (size_ip < 20) 
     { Wrg_IpH++;  T_Wrg_IpH++; }  
     if (size_tcp < 20) 
     { Wrg_TcpH++; T_Wrg_TcpH++; } 
      
   }  
 
    // Check to see if we have an ip packet  
    if (ntohs (eptr->ether_type) == ETHERTYPE_IP) 
    { 
      strcpy(Pack[Cnt].Net_P,"IP"); 
      Ip++; 
      T_IP++;  
    } 
    else  if (ntohs (eptr->ether_type) == ETHERTYPE_ARP) 
    { 
      strcpy(Pack[Cnt].Net_P,"ARP"); 
      Arp++; 
      T_ARP++;   
    }  
    else 
    {   
      strcpy(Pack[Cnt].Net_P,"OTH"); 
      OTH_Net1++;  
      T_OTH_Net++; 
    } 
 
   // Source and Destination MAC address. 
   strcpy(Pack[Cnt].Src_MAC,(char*)ether_ntoa(eptr->ether_shost)); 
   strcpy(Pack[Cnt].Dest_MAC,(char*)ether_ntoa(eptr->ether_dhost)); 
 
//======================== IP header Info ============================= 
 
   
 
  strcpy(Pack[Cnt].Src_IP,""); 
  strcpy(Pack[Cnt].Dest_IP,""); 
 
  strcpy(Pack[Cnt].Src_IP,inet_ntoa(ip->ip_src));   //Source IP 
  strcpy(Pack[Cnt].Dest_IP,inet_ntoa(ip->ip_dst));  // Destination IP 
 
 
  if(strstr(Pack[Cnt].Src_IP,"255") || strstr(Pack[Cnt].Dest_IP,"255") ) 
  { 
   BdCast++;  T_BdCast++; 
  } 
 
//===================== TCP & UDP header Info ======================== 
 
    udp = (struct sniff_udp*) (pckt + SIZE_ETHERNET + size_ip); 
 
  // Determine protocol  
   switch(ip->ip_p)  
   { 
     // IPPROTO_TCP = 6,        Transmission Control Protocol.   
     case IPPROTO_TCP:                        
         strcpy(Pack[Cnt].Trans_P,"TCP"); 
             Pack[Cnt].Src_Port = ntohs(tcp->th_sport);   // Src Port 
             Pack[Cnt].Dest_Port = ntohs(tcp->th_dport);  // Dest Port 
             Tcp++; 
             T_TCP++; 
     break; 
 
     // IPPROTO_UDP = 17,    User Datagram Protocol.                  
     case IPPROTO_UDP:                                    
            strcpy(Pack[Cnt].Trans_P,"UDP"); 
            Pack[Cnt].Src_Port = ntohs(udp->source);     // Src Port 
            Pack[Cnt].Dest_Port = ntohs(udp->dest);    // Dest Port 
            Udp++; 
            T_UDP++;      
     break; 
 
     // IPPROTO_ICMP = 1,         Internet Control Message Protocol.       
     case IPPROTO_ICMP:                
        strcpy(Pack[Cnt].Trans_P,"ICMP");       
            //strcpy(Pack[Cnt].Trans_P,"OTH"); 
            Pack[Cnt].Src_Port = 0;     // Source Port 
            Pack[Cnt].Dest_Port = 0;    // Destination Port                 
            Icmp++; 
            //OTH_Trans1++; 
            T_ICMP++; 
            //T_OTH_Trans++; 
 
     break; 
    
     default: 
           strcpy(Pack[Cnt].Trans_P,"OTH"); 
           Pack[Cnt].Src_Port = 0;     // Src Port 
           Pack[Cnt].Dest_Port = 0;    // Dest Port            
           OTH_Trans1++;  T_OTH_Trans++; 
     break; 
  } 
 
  Cnt++; 
   
  return; 
} 

how to do from c file to link with sqlite to store into databse?thanks

---

### Post by Tony Flury on 2013-05-01
ok - a few things : 

Always when posting code embedd then in code tags - it is much nicer to read

Are you asking about how you use the sqlite libarary in C or how you should store your data in the database : 

for sqlite in C - a quick google search turned up this [http://www.sqlite.org/quickstart.html](http://www.sqlite.org/quickstart.html)

For how to store your data - it all depends what you are storing it for, and how you intend to use that store - giving that some thought will show you what tables you need - what columns each table will need, what the unique keys are and what are the relationships between the different tables.

---

### Post by Newbie89 on 2013-05-01
> **Tony Flury said:**
> ok - a few things : 

Always when posting code embedd then in code tags - it is much nicer to read

Are you asking about how you use the sqlite libarary in C or how you should store your data in the database : 

for sqlite in C - a quick google search turned up this [http://www.sqlite.org/quickstart.html](http://www.sqlite.org/quickstart.html)

For how to store your data - it all depends what you are storing it for, and how you intend to use that store - giving that some thought will show you what tables you need - what columns each table will need, what the unique keys are and what are the relationships between the different tables.

Hi,
sorry for the info not clear,I wanna ask how to store data in the database.The packet data is captured from the HUB to the Host,I need to link them to store directly to my database.
My table will consist of [COLOR=#000000]*char Src_MAC, Dest_MAC, *[/COLOR][COLOR=#000000]*Net_P,Trans_P*[/COLOR][COLOR=#000000]*,Src_IP, Dest_IP ,*[/COLOR][COLOR=#000000][I]Src_Port,Dest_Port,  and Cap_Bytes...
[/I][/COLOR]I can do it manually between C and sqlite using insert query...
But for link with live data,I'm not have any idea to start...

---

### Post by Tony Flury on 2013-05-02
you will need to design your tables first - what are the types of each of your pieces of information ?
You will need to decide if your database will exist before your code runs or whether your code will try to create the database first.

My suggestion is to read the link i provided - and make a simple application that opens a database, creates a table, and then stores some information in that table. Once you have the basics down, it will be more obvious how to make it work in your application.

I have never used sqlite with C so i can't give you example code, but it would be better if you learn by making your own test application as above.

---

### Post by Newbie89 on 2013-05-02
> **Tony Flury said:**
> you will need to design your tables first - what are the types of each of your pieces of information ?
You will need to decide if your database will exist before your code runs or whether your code will try to create the database first.

My suggestion is to read the link i provided - and make a simple application that opens a database, creates a table, and then stores some information in that table. Once you have the basics down, it will be more obvious how to make it work in your application.

I have never used sqlite with C so i can't give you example code, but it would be better if you learn by making your own test application as above.

Thanks for your advice...I have a tutorial which store data manually using sqlite3 and c...I can create table and store data using insert query to make it...now I'm doing enhancement on network traffic monitoring system...which need to link from where the data capture and store into the database...my problem now is dunno to link the entm.c file with my sqlite file...

---

