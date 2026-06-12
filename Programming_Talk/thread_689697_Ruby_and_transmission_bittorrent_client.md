---
title: "Ruby and transmission bittorrent client"
date: 2008-02-06
forum: Programming Talk
---

### Post by milosz.galazka on 2008-02-06
Hello,

I tried to communicate with transmission-daemon - [http://www.transmissionbt.com/](http://www.transmissionbt.com/)  using Ruby. I tried to copy solution from Cluth - [http://clutchbt.com/](http://clutchbt.com/) but I cannot get encoder working in right way ;/ there is problem with with one closing "e" from array or dict/hash or integer.  It looks like decoder works fine.

Maybe someone could help or point me my mistakes


```

#!/usr/bin/ruby


class BEncodeSerializer


  def Serialize(mixed)
    p "m: " + mixed.to_s + "  " + mixed.class.to_s
    case mixed.class.to_s
    when "String"
      encode_string(mixed)
    when "Bignum"
      encode_fixnum(mixed)
    when "Fixnum"
      encode_fixnum(mixed)
    when "Array"
      encode_array(mixed)
    when "Hash"
      encode_hash(mixed)
    end
  end

  def encode_string(mixed)
    mixed.size.to_s + ":" +  mixed
  end

  def encode_fixnum(mixed)
    ret="i" + mixed.to_s + "e"
    ret
  end

  def encode_array(mixed)
    ret="l"
    mixed.each do |var|
      if var.class.to_s != "Array" and var.class.to_s != "Hash" and (var.to_i).to_s==var.to_s
        ret = ret + Serialize(var.to_i).to_s
      else
        if var.class.to_s == "Array"
          ret = ret + Serialize(var).to_s
        else
          if var.class.to_s == "Hash"
            ret = ret + Serialize(var).to_s
          else 
            ret = ret + Serialize(var.to_s).to_s
          end
        end
      end
    end
    ret = ret + "e"
    p "a: " + ret
    ret
  end

  def encode_hash(mixed)
    ret="d"
    mixed.each do |key,var|
      p "KK: " + key.to_s + " " + var.to_s
      ret = ret + Serialize(key).to_s
      ret = ret + Serialize(var).to_s
    end
    ret = ret + "e" 
    p "h:" + ret.to_s
    ret
  end
end

class BEncodeUnserializer
  @source=""
  @source_length=0
  @position=0

  def Unserialize(str)
    @source=str
    @position=0
    @source_length=@source.size
    bDecode
  end

  def bDecode
    case pgetChar
    when "i"
      @position=@position+1
      ret=decode_fixnum
    when "l"
      @position=@position+1
      ret=decode_array
    when "d"
      @position=@position+1
      ret=decode_hash
    else
      ret=decode_string
    end
    ret
  end


  def decode_string
    stringLenStr=""
    ret=""

    if (!@source[(@position)..(@position)])
      false
    end

    stringLenStr=@source[(@position)..(@position)]

    @position=@position+1
    startPos=@position

    while(pgetChar != ":")
      actChr=pgetChar
      if actChr == nil
        break
      end
      stringLenStr=stringLenStr + actChr
      @position=@position+1
      startPos=startPos+1
    end  
    ret=@source[startPos+1..@position.to_i+(stringLenStr.to_i)]
    @position=@position+stringLenStr.to_i+1
    ret
  end

  def decode_fixnum
    pos_e=@source.index("e",@position)
    ret=@source[(@position)..(pos_e-1)]
    @position=pos_e+1
    p ret
    ret
  end

  def decode_array
    arr=Array.new
    while(@source[@position..@position] != "e" and  @position < @source_length)
      val=bDecode
      if val == nil
        val="0"
      end
      arr.insert(-1,val)
    end
    @position=@position+1+1;
    arr 
  end

  def decode_hash
    hash=Hash.new
    if(pgetChar != "e")
      key=bDecode
      val=bDecode
      hash[key] = val
    end
    @position=@position-1;
    hash
  end

  def pgetChar
    if @source.empty? 
      false
    end
    if @position >= @source_length
     false
    end
    @source[@position..@position]
  end
end

test=["get-status", {"id"=>["1"]}, "type", ["completed", "download-speed", "download-total", "error", "error-message", "eta", "id", "peers-downloading", "peers-from", "peers-total", "peers-uploading", "running", "state", "swarm-speed", "tracker", "scrape-completed", "scrape-leechers", "scrape-seeders", "upload-speed", "upload-total"], "1202257539"]
# "l10:get-statusd2:idli1ee4:typel9:completed14:download-speed14:download-total5:error13:error-message3:eta2:id17:peers-downloading10:peers-from11:peers-total15:peers-uploading7:running5:state11:swarm-speed7:tracker16:scrape-completed15:scrape-leechers14:scrape-seeders12:upload-speed12:upload-totaleei1202257539ee"


encoder=BEncodeSerializer.new
decoder=BEncodeUnserializer.new

encoded_test=encoder.Serialize(test)

decoded_test=decoder.Unserialize(encoded_test)
p "---------- test ----------"
p test
p encoded_test
p decoded_test

p "---------- check ----------"
p decoder.Unserialize("l10:get-statusd2:idli1ee4:typel9:completed14:download-speed14:download-total5:error13:error-message3:eta2:id17:peers-downloading10:peers-from11:peers-total15:peers-uploading7:running5:state11:swarm-speed7:tracker16:scrape-completed15:scrape-leechers14:scrape-seeders12:upload-speed12:upload-totaleei1202257539ee")

```

Thanks for any suggestions!

---

### Post by fguillen on 2012-11-20
I have just implemented a very simple ruby gem to wrapper the Transmission RPC API:

* [https://github.com/fguillen/TransmissionApi](https://github.com/fguillen/TransmissionApi)

---

