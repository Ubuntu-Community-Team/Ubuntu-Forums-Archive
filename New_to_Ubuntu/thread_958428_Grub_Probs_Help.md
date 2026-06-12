---
title: "Grub Probs Help"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by omkarphadke on 2008-10-25
Hello Guys I m having a probs in Grub.I had installed Windows Xp n Ubuntu 8.04 it was running 5n until I had installed RHEL 5.RHEL 5 overwrote Ubuntu Grub n now I can boot from Windows Xp n RHEL 5 but there is no entry of Ubuntu 8.10 which I had updated... 
                           I had updated the /etc/grub.conf of RHEL 5 by adding 4 lines of Ubuntu + chain loader but it didn't make up...I would really happy if anyone Solves my probs plz... I want my Ipred beta back plz...


    
    

    
    

    Hello Guys I m having a probs in Grub.I had installed Windows Xp n Ubuntu 8.04 it was running 5n until I had installed RHEL 5.RHEL 5 overwrote Ubuntu Grub n now I can boot from Windows Xp n RHEL 5 but there is no entry of Ubuntu 8.10 which I had updated...

      
      

        
Server not found

      

      
      
      

      
        
        

          

Firefox can't find the server at [www.earch.php](www.earch.php).

        


        
        


    *   Check the address for typing errors such as
          ww.example.com instead of
          [www.example.com](www.example.com)

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.




      

    
    

    
    

    
      
      

        
Server not found

      

      
      
      

      
        
        

          

Firefox can't find the server at [www.earch.php](www.earch.php).

        


        
        


    *   Check the address for typing errors such as
          ww.example.com instead of
          [www.example.com](www.example.com)

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.




      


      
      

    


    
    

  


      
      

    


    
    

  
    
    

    
    

    
      
      

        
Server not found

      

      
      
      

      
        
        

          

Firefox can't find the server at [www.earch.php](www.earch.php).

        


        
        


    *   Check the address for typing errors such as
          ww.example.com instead of
          [www.example.com](www.example.com)

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.




      


      

    
    

    
    

    
      
      

        
Server not found

      

      
      
      

      
        
        

          

Firefox can't find the server at [www.earch.php](www.earch.php).

        


        
        


    *   Check the address for typing errors such as
          ww.example.com instead of
          [www.example.com](www.example.com)

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.




      


      

    
    

    
    

    
      
      

        
Server not found

      

      
      
      

      
        
        

          

Firefox can't find the server at [www.earch.php](www.earch.php).

        


        
        


    *   Check the address for typing errors such as
          ww.example.com instead of
          [www.example.com](www.example.com)

    *   If you are unable to load any pages, check your computer's network
          connection.

    *   If your computer or network is protected by a firewall or proxy, make sure
          that Firefox is permitted to access the Web.

---

### Post by Xiong Chiamiov on 2008-10-26
You should probably edit your post to remove all of the Firefox 404s from it.  They don't need to be there, and it makes me have to scroll much more than I'd like.

The problem is that you installed the bootloader to the MBR (master boot record) both times.  If you had installed Fedora's grub to whatever partition you installed Fedora onto, then you could just chainload it from Ubuntu's.

However, since you don't have grub installed on Ubuntu's partition, either, you'll have to either a) reinstall grub on Ubuntu's partition or b) add Ubuntu's boot parameters directly into Fedora's grub menu.  I'll leave the first for you to search for; there's plenty of information [around the web]("http://www.google.com/search?hl=en&q=reinstall%20grub&aq=f&oq=").  For the second, you'll need to mount your Ubuntu partition in Fedora, then copy+paste the lines from it into Fedora's menu.lst.

---

