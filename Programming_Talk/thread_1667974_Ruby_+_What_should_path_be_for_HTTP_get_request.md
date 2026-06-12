---
title: "Ruby + What should path be for HTTP get request?"
date: 2011-01-15
forum: Programming Talk
---

### Post by nova47 on 2011-01-15
So I've been teaching myself some socket programming but I've gotten hung up on one part. If you're familiar with the wget utility you know you can do something like wget [http://www.airforce.com](http://www.airforce.com) and you don't have to enter a path or anything. I've written the following Ruby script that grabs all the servers listed on a webpage:

[php]

require 'net/http'

class Enumerate
  
  hostname = ARGV[0].delete "\n"

  if ARGV[1] != nil
    path = ARGV[1].delete "\n"
  else
    process.exit(0)
  end
  
  lines = [], flines = []
  
  http = Net::HTTP.new(hostname)      # Create a connection
  headers, body = http.get(path)      # Request the file
  if headers.code == "200"            # Check the status code   
    body.each { |line|
      line.chomp!; lines << line.split('/')[2] if line.include? "href="
    }
    
    server = ARGV[0]
    server = server.slice(4..-1)
    
    lines. each do |line|
      flines << line.delete( " \" ") if (line != nil and line.include? server)
    end
    
    flines = flines.uniq.sort
    
    flines.each do |line|
      puts "Hostname: " + line + " ----- IP Address: " + IPSocket.getaddress(line.to_s.chomp)
    end
    
  else                                
    puts "#{headers.code} #{headers.message}" 
  end
  
end

[/php]

Problem is what do you do for a website that doesn't have a visible path (such as airforce.com)? For instance if you go to a website icq.com it automatically appends /en.html so you can tell what the path is. So for a website such as airforce.com what is the path? I've tried stuff like ///airforce.com but it just returns 302 found.

---

### Post by nova47 on 2011-01-16
I found the answer to my own question and it was stupid obvious. (You would think for someone who uses linux a lot this would have been even more obvious). "/" is considered a path so the path for a website such as airforce.com is simply /.

---

