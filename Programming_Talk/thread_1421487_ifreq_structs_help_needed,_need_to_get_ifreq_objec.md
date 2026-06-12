---
title: "ifreq structs help needed, need to get ifreq object given interface name"
date: 2010-03-04
forum: Programming Talk
---

### Post by TMagic*04 on 2010-03-04
I'm trying to write a function to discover a computers network interfaces. Where for example given eth1 I can get its hwAdd and IP. The way i'm trying is to grab an ifconf object and iterate through it to get each interface and inspect them seperatley. Although for some reason it doesn't quite work and only returns interface: lo (which isnt even the first one when listed in ifconfig!). Does anyone an easier way of doing this? or what could be going wrong in my code? (posted below)


From Header: 
#define MAX(x,y) ((x) > (y) ? (x) : (y)) 
#define SIZE(p) MAX((sizeof((p).sa_data) + sizeof((p).sa_family), sizeof(p)) //sizeof(p).sa_data) + sizeof((p).sa_family) is my attempt to bypass there being no sa_len attached to a sockaddr which should give the structs full length

======
From CPP file: 

/*To be used at startup. Node will inspect its ifconfig object 
 * in order to determine hwaddr & IP (if assigned) 
 */
int NeighbourAddressFinder:: defineSelf()
{
  struct ifconf ifc;
  char *cp,*cplim,addr[INET6_ADDRSTRLEN];
  struct ifreq *ifr;
  int    fd, size = 1;
  void* converter;
  string mi0 = "eth1", mi1 = "wlan0";//where mi == Mesh Interface
  
  try
  {
  
    //prepare socket used to channel ifreq struct
    if((fd = socket(AF_INET, SOCK_DGRAM, IPPROTO_IP)) < 0)
    {
      perror("socket:");
      return -1;
    }

    //prep data structs    
    char *f = new char[mi0.size()];
    char *s = new char[mi1.size()];
    memcpy(f, mi0.c_str(), mi0.size());
    memcpy(s, mi1.c_str(), mi1.size());
  
    if(allocBufferSize(fd, &ifc) < 0)
    {
      cout << "ERROR allocating buffers" << endl;
      return -1;
    }
    
    ifr = ifc.ifc_req;
    cp=(char *)ifc.ifc_req;
    cout << "ifc.ifc_len" << ifc.ifc_len;
    cplim=cp+ifc.ifc_len;
    for(;cp<cplim;cp+=(sizeof(ifr->ifr_name) + SIZE(ifr->ifr_addr))){
        /* NOTE: You cannot just increment cp with sizeof(struct ifreq)
         * as structures returned are of different length.
         */
        cout <<"CP " << cp << "CPLIM " << cplim << endl;
       // cout << "calculation test " << SIZE(ifr->ifr_addr) << endl;
        ifr=(struct ifreq *)cp;
        printf("%s :",ifr->ifr_name);
     }
     
      return 1;

  }
  catch(exception& e)
  {
    cout << NERROR_MESSAGE << "| - | @defineSelf " << e.what() << endl;
    return -1;
  }
}

int NeighbourAddressFinder:: allocBufferSize(int fd, struct ifconf *ifc)
{
  try
  {
    int ret=-1,bsz=sizeof(struct ifreq);
    int prevsz=bsz;
    ifc->ifc_req=NULL;
    ifc->ifc_len=bsz;
    do{
       ifc->ifc_req=(struct ifreq *)realloc(ifc->ifc_req,bsz);
       if(!ifc->ifc_req){
         perror("Malloc failed :");
         return ret;
       }
       ifc->ifc_len=bsz;
       ret=ioctl(fd,SIOCGIFCONF,(caddr_t)ifc);
       if(ret==-1){
          perror("Error getting size of interface :");
          return ret;
       }
      if(prevsz==ifc->ifc_len)
        break;
      else{
         bsz*=2;
         prevsz=(0==ifc->ifc_len ? bsz : ifc->ifc_len) ;
      }
    }while(1);
    ifc->ifc_req=(struct ifreq *)realloc(ifc->ifc_req,prevsz);
    return ifc->ifc_len;

    
  }
  catch(exception& e)
  {
    cout << NERROR_MESSAGE << "| - | @setSelf | " << e.what() << endl;
    return -1;
  }
}

---

### Post by TMagic*04 on 2010-03-04
I fixed it by recoding in a much simpler way:

ifc.ifc_len=sizeof(buff);
    ifc.ifc_buf = buff;
    if(0 == ioctl(fd, SIOCGIFCONF, &ifc))
    {
      for(int c=0; c<ifc.ifc_len/sizeof(struct ifreq); c++)
      {
        ifr = &ifc.ifc_req[c];
        
        cout << ifr->ifr_name << endl;
      }
    }

If anyones interested this should list all your interfaces and from there by probing the ifr object you can get the rest of the information. If you weren't then sorry for wasting your time

---

