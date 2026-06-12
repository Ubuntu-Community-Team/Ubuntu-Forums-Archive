---
title: "extracting useful info out of tcpdump hex data"
date: 2009-02-12
forum: Programming Talk
---

### Post by bhaskar_goel on 2009-02-12
i am trying to write a c programme which takes standard tcpdump output and gives me wireshark like output with mac destination ,source etc. i am stuck on the info field:- how do i take the hexdata which comes inside the packet and extract useful information out of it. any ideas. here is my programme.


#include <stdio.h>

int main()
{
	char timestamp[15]="";
	char srcmac[20]="";
	char dstmac[20]=""; 
	char srcip[15]="";
	char dstip[15]="";
	char srcport[5]="";
	char dstport[5]="";
	char length[4]="";
	char data[100]="";
	char protocol[6]="";
	char line[230];
	char opline[100];
	char c;
	int i=0;
	int j=0;
	//int k=0;
	int dotcount=0;
	FILE *fin;
	FILE *fout;
	fin=fopen("/home/bhaskar/dev_stuff/C_collect.txt","r");
	fout=fopen("/home/bhaskar/Desktop/testres.txt","w");
	if(!fin) 	printf("failed to open");
	if(!fout) printf("failed to open write");
	while(fgets(line, 230, fin)!=NULL)
	{
		//printf("%s",line);
		i=0;j=0;
		if(isdigit(line[0])) // its not the data output line
		{
			while(line[i]!=' ')
			{
					opline[j++]=line[i++];	//timestamp
			}
			opline[j++]=',';
			i++; //eat space
			while(line[i]!=' ')
			{
					opline[j++]=line[i++];	 //macsrc
			}
			opline[j++]=',';
			
			i=i+3;  //  eat space > space
			
			while(line[i]!=',')
			{
					opline[j++]=line[i++];	  //macdst
			}
			opline[j++]=',';
			
			i=i+12; //eat , space ethertype space
			
			while(line[i]!=' ')
			{
					//protocol[k++]=line[i];
					opline[j++]=line[i++];	 // protocol
			}
			opline[j++]=',';
			
			i=i+18; //eat space (0x8...etc
			//printf("%c",opline[j-2]);
			switch(opline[j-2])
			{
				case '4':
					while(line[i]!=':')
					{
							opline[j++]=line[i++]; //length	
					}
					opline[j++]=',';
			
					i+=2;
					while(dotcount<4)
					{
						opline[j++]=line[i++];   //ip source
						if(line[i]=='.')
							dotcount++;
					}
					opline[j++]=',';
					dotcount=0;
					i++;		
					
					while(line[i]!=' ')
					{
							opline[j++]=line[i++];	 // port source
					}
					opline[j++]=',';
					
					i+=3;
					
					while(dotcount<4)
					{
						opline[j++]=line[i++];   //ip dst
						if(line[i]=='.')
							dotcount++;
					}
					opline[j++]=',';
					dotcount=0;
					i++;		
					
					while(line[i]!=':')
					{
							opline[j++]=line[i++];	 // port dst
					}
					opline[j++]=',';
					
					
					
					
					
					
					
					
					
					
					
					
					
					opline[j]='\0';
					
					fputs(opline,fout);
					fputs("\n",fout);
					break;
				
				
				
				
				
				
				
				
				case 'P':
					 while(line[i]!=':')
					   {
					   	  opline[j++]=line[i++];
					   	}
					   	opline[j++]=',';
					 
					 while(line[i]!='\n')
					   {
					   	opline[j++]=line[i++];
					   }
					
					 
					 opline[j]='\0';
					
					fputs(opline,fout);
					fputs("\n",fout);  	   
					   
					break;
					
			}
		}
		
		
	}
	//fputs(opline,fout);
	return 0;
}

and here is the text file which stores the tcpdump output:-

10:06:56.220436 00:15:17:98:d0:9e > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: arp who-has 15.15.151.15 (ff:ff:ff:ff:ff:ff) tell 15.15.151.15
	0x0000:  0001 0800 0604 0001 0015 1798 d09e 0f0f
	0x0010:  970f ffff ffff ffff 0f0f 970f 0000 0000
	0x0020:  0000 0000 0000 0000 0000 0000 0000
10:06:56.563181 00:17:31:70:cb:e6 > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 92: 172.31.5.55.137 > 172.31.255.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
	0x0000:  4500 004e 4bc3 0000 8011 9166 ac1f 0537
	0x0010:  ac1f ffff 0089 0089 003a 9553 8322 0110
	0x0020:  0001 0000 0000 0000 2046 4546 4444 4144
	0x0030:  4143 4f45 4646 4445 4646 4543 4f45 4445
	0x0040:  5045 4e43 4143 4141 4100 0020 0001
10:06:56.646740 00:1e:8c:cd:ea:03 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: arp who-has 172.31.0.141 tell 172.31.2.4
	0x0000:  0001 0800 0604 0001 001e 8ccd ea03 ac1f
	0x0010:  0204 0000 0000 0000 ac1f 008d 0000 0000
	0x0020:  0000 0000 0000 0000 0000 0000 0000
10:06:56.713152 00:30:48:28:ca:82 > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 92: 172.31.1.137.137 > 172.31.255.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
	0x0000:  4500 004e fae5 0000 8011 e5f1 ac1f 0189
	0x0010:  ac1f ffff 0089 0089 003a 2526 fdfd 0110
	0x0020:  0001 0000 0000 0000 2046 4845 5046 4345
	0x0030:  4c45 4846 4345 5046 4646 4143 4143 4143
	0x0040:  4143 4143 4143 4142 4d00 0020 0001
10:06:56.784483 00:18:f3:22:18:23 > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 243: 172.31.5.36.138 > 172.31.255.255.138: NBT UDP PACKET(138)
	0x0000:  4500 00e5 5e83 0000 8011 7e22 ac1f 0524
	0x0010:  ac1f ffff 008a 008a 00d1 7ced 110e 8582
	0x0020:  ac1f 0524 008a 00bb 0000 2045 4f46 4546
	0x0030:  4145 4444 4444 4743 4143 4143 4143 4143
	0x0040:  4143 4143 4143 4143 4143 4100 2046 4845
	0x0050:  4a45 4f45 4545 5046 4846 4443 4e45 4445
	0x0060:  4443 4143 4143 4143 4143 4142 4e00 ff53
	0x0070:  4d42 2500 0000 0000 0000 0000 0000 0000
	0x0080:  0000 0000 0000 0000 0000 0000 0000 1100
	0x0090:  0021 0000 0000 0000 0000 00e8 0300 0000
	0x00a0:  0000 0000 0021 0056 0003 0001 0000 0002
	0x00b0:  0032 005c 4d41 494c 534c 4f54 5c42 524f
	0x00c0:  5753 4500 0100 80fc 0a00 4e54 5043 3336
	0x00d0:  0000 2a00 2000 6600 7200 0501 0310 0000
	0x00e0:  0f01 55aa 00
10:06:56.821653 00:a0:c9:06:95:99 > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 92: 172.31.1.21.137 > 172.31.255.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
	0x0000:  4500 004e 74e8 0000 8011 6c63 ac1f 0115
	0x0010:  ac1f ffff 0089 0089 003a 4dd4 c0c0 0110
	0x0020:  0001 0000 0000 0000 2045 4e45 4245 4a45
	0x0030:  4d43 4f45 4746 4645 4446 4646 4b46 4b46
	0x0040:  4a43 4143 4143 4141 4100 0020 0001
10:06:56.832696 00:09:3d:00:c4:cb > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: arp who-has 172.31.1.237 tell 172.31.1.175
	0x0000:  0001 0800 0604 0001 0009 3d00 c4cb ac1f
	0x0010:  01af 0000 0000 0000 ac1f 01ed 0000 0000
	0x0020:  0000 0000 0000 0000 0000 0000 0000
10:06:57.056877 00:1e:8c:c7:43:86 > 00:18:71:e5:47:82, ethertype ARP (0x0806), length 42: arp who-has 172.31.1.227 tell 172.31.9.14
	0x0000:  0001 0800 0604 0001 001e 8cc7 4386 ac1f
	0x0010:  090e 0000 0000 0000 ac1f 01e3
10:06:57.057023 00:18:71:e5:47:82 > 00:1e:8c:c7:43:86, ethertype ARP (0x0806), length 60: arp reply 172.31.1.227 is-at 00:18:71:e5:47:82
	0x0000:  0001 0800 0604 0002 0018 71e5 4782 ac1f
	0x0010:  01e3 001e 8cc7 4386 ac1f 090e 0000 0000
	0x0020:  0000 0000 0000 0000 0000 0000 0000
10:06:57.252827 00:11:d8:0a:78:58 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: arp who-has 172.31.1.1 tell 172.31.2.3
	0x0000:  0001 0800 0604 0001 0011 d80a 7858 ac1f
	0x0010:  0203 0000 0000 0000 ac1f 0101 0000 0000
	0x0020:  0000 0000 0000 0000 0000 0000 0000
10:06:57.260825 00:11:d8:0a:78:58 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: arp who-has 172.31.1.212 tell 172.31.2.3
	0x0000:  0001 0800 0604 0001 0011 d80a 7858 ac1f
	0x0010:  0203 0000 0000 0000 ac1f 01d4 0000 0000
	0x0020:  0000 0000 0000 0000 0000 0000 0000
10:06:57.462266 00:30:48:28:ca:82 > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 92: 172.31.1.137.137 > 172.31.255.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
	0x0000:  4500 004e fb01 0000 8011 e5d5 ac1f 0189
	0x0010:  ac1f ffff 0089 0089 003a 2526 fdfd 0110
	0x0020:  0001 0000 0000 0000 2046 4845 5046 4345
	0x0030:  4c45 4846 4345 5046 4646 4143 4143 4143
	0x0040:  4143 4143 4143 4142 4d00 0020 0001
10:06:57.571592 00:a0:c9:06:95:99 > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 92: 172.31.1.21.137 > 172.31.255.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
	0x0000:  4500 004e 75e8 0000 8011 6b63 ac1f 0115
	0x0010:  ac1f ffff 0089 0089 003a 4dd4 c0c0 0110
	0x0020:  0001 0000 0000 0000 2045 4e45 4245 4a45
	0x0030:  4d43 4f45 4746 4645 4446 4646 4b46 4b46
	0x0040:  4a43 4143 4143 4141 4100 0020 0001
10:06:57.590520 00:05:01:f9:28:00 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: arp who-has 172.31.2.1 tell 172.31.1.250
	0x0000:  0001 0800 0604 0001 0005 01f9 2800 ac1f
	0x0010:  01fa 0000 0000 0000 ac1f 0201 0000 0000
	0x0020:  0000 0000 0000 0000 0000 0000 0000
10:06:57.832751 00:09:3d:00:c4:cb > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: arp who-has 172.31.1.237 tell 172.31.1.175
	0x0000:  0001 0800 0604 0001 0009 3d00 c4cb ac1f
	0x0010:  01af 0000 0000 0000 ac1f 01ed 0000 0000
	0x0020:  0000 0000 0000 0000 0000 0000 0000
10:06:57.903188 00:05:01:f9:28:00 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: arp who-has 172.31.1.12 tell 172.31.1.250
	0x0000:  0001 0800 0604 0001 0005 01f9 2800 ac1f
	0x0010:  01fa 0000 0000 0000 ac1f 010c 0000 0000
	0x0020:  0000 0000 0000 0000 0000 0000 0000
10:06:58.112146 00:05:01:f9:28:00 > ff:ff:ff:ff:ff:ff, ethertype ARP (0x0806), length 60: arp who-has 172.31.1.0 tell 172.31.1.250
	0x0000:  0001 0800 0604 0001 0005 01f9 2800 ac1f
	0x0010:  01fa 0000 0000 0000 ac1f 0100 0000 0000
	0x0020:  0000 0000 0000 0000 0000 0000 0000
10:06:58.212265 00:30:48:28:ca:82 > ff:ff:ff:ff:ff:ff, ethertype IPv4 (0x0800), length 92: 172.31.1.137.137 > 172.31.255.255.137: NBT UDP PACKET(137): QUERY; REQUEST; BROADCAST
	0x0000:  4500 004e fb0a 0000 8011 e5cc ac1f 0189
	0x0010:  ac1f ffff 0089 0089 003a 2526 fdfd 0110
	0x0020:  0001 0000 0000 0000 2046 4845 5046 4345
	0x0030:  4c45 4846 4345 5046 4646 4143 4143 4143
	0x0040:  4143 4143 4143 4142 4d00 0020 0001

if anyone can help with a hint or point to the right direction ,that would be nice

---

