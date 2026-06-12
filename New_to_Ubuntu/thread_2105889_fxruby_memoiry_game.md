---
title: "fxruby memoiry game"
date: 2013-01-17
forum: New to Ubuntu
---

### Post by makoshi563 on 2013-01-17
For my intro to computer programming class I need to make a memory game using fxruby.

This is my code so far. I need to figure out how to make it so when two buttons are clicked the rest cannot be clicked. If the two buttons match then the back color becomes blue, but if they do not match then it flip back to nil.
require 'fox16'
require 'rubygems'


include Fox


class MemoryGameWindow < FXMainWindow
	def initialize(app)
		super(app,"Memory Game", :width => 670, :height => 670)
		
		@clickNumber=0
		@buttonArray=[]
		@score = 0
		
		
		self.title = "Memory Game: " + @score.to_s
	
		
		@board=FXMatrix.new(self, 6, :opts => MATRIX_BY_COLUMNS|LAYOUT_FILL, :vSpacing => 0, :hSpacing => 0)
		
		dogFile = File.open("dog.jpg","rb")
		dog = FXJPGIcon.new(app, dogFile.read)
		dog.scale(100,100)
		dogFile.close
		button=PictureButton.new(@board,nil,dog,1)
		
		deathFile = File.open("death.jpg","rb")
		death = FXJPGIcon.new(app, deathFile.read)
		death.scale(100,100)
		deathFile.close
		button = PictureButton.new(@board,nil,death,2)
		
		earthFile = File.open("earth.png","rb")
		earth = FXPNGIcon.new(app, earthFile.read)
		earth.scale(100,100)
		earthFile.close
		button = PictureButton.new(@board,nil,earth,3)
		
		fireFile = File.open("fire.png","rb")
		fire = FXPNGIcon.new(app, fireFile.read)
		fire.scale(100,100)
		fireFile.close
		button = PictureButton.new(@board,nil,fire,4)
		
		flowerFile = File.open("flower.jpg","rb")
		flower = FXJPGIcon.new(app, flowerFile.read)
		flower.scale(100,100)
		flowerFile.close
		button = PictureButton.new(@board,nil,flower,5)
		
		heartFile = File.open("heart.jpg","rb")
		heart = FXJPGIcon.new(app,heartFile.read)
		heart.scale(100,100)
		heartFile.close
		button = PictureButton.new(@board,nil,heart,6)
		
		iceFile = File.open("ice.png","rb")
		ice = FXPNGIcon.new(app,iceFile.read)
		ice.scale(100,100)
		iceFile.close
		button = PictureButton.new(@board,nil,ice,7)
		
		lifeFile = File.open("life.png","rb")
		life = FXPNGIcon.new(app,lifeFile.read)
		life.scale(100,100)
		lifeFile.close
		button = PictureButton.new(@board,nil,life,9)
		
		lightFile = File.open("light.png","rb")
		light = FXPNGIcon.new(app,lightFile.read)
		light.scale(100,100)
		lightFile.close
		button = PictureButton.new(@board,nil,light,10)
		
		loveFile = File.open("love.jpg","rb")
		love = FXJPGIcon.new(app,loveFile.read)
		love.scale(100,100)
		loveFile.close
		button = PictureButton.new(@board,nil,love,11)
		
		manFile = File.open("man.jpg","rb")
		man = FXJPGIcon.new(app,manFile.read)
		man.scale(100,100)
		manFile.close
		button = PictureButton.new(@board,nil,man,8)
		
		personFile = File.open("person.jpg","rb")
		person = FXJPGIcon.new(app,personFile.read)
		person.scale(100,100)
		personFile.close
		button = PictureButton.new(@board,nil,person,12)
		
		riverFile = File.open("river.jpg","rb")
		river = FXJPGIcon.new(app,riverFile.read)
		river.scale(100,100)
		riverFile.close
		button = PictureButton.new(@board,nil,river,13)
		
		womanFile = File.open("woman.png","rb")
		woman = FXPNGIcon.new(app,womanFile.read)
		woman.scale(100,100)
		womanFile.close
		button = PictureButton.new(@board,nil,woman,14)
		
		samuraiFile = File.open("samurai.png","rb")
		samurai = FXPNGIcon.new(app,samuraiFile.read)
		samurai.scale(100,100)
		samuraiFile.close
		button = PictureButton.new(@board,nil,samurai,15)
		
		rainFile = File.open("rain.jpg","rb")
		rain = FXJPGIcon.new(app,rainFile.read)
		rain.scale(100,100)
		rainFile.close
		button = PictureButton.new(@board,nil,rain,16)
		
		windFile = File.open("wind.png","rb")
		wind = FXPNGIcon.new(app,windFile.read)
		wind.scale(100,100)
		windFile.close
		button = PictureButton.new(@board,nil,wind,17)
		
		moneyFile = File.open("money.png","rb")
		money = FXPNGIcon.new(app,moneyFile.read)
		money.scale(100,100)
		moneyFile.close
		button = PictureButton.new(@board,nil,money,18)
		
		money_button= TextButton.new(@board,"Money",18)
		money_button.setFont(FXFont.new(app,"Times New Roman",25,FONTSLANT_ITALIC))
	
		wind_button= TextButton.new(@board,"Wind",17)
		wind_button.setFont(FXFont.new(app,"Times New Roman",25,FONTSLANT_ITALIC))
		
		rain_button= TextButton.new(@board,"Rain",16)
		rain_button.setFont(FXFont.new(app,"Times New Roman",25,FONTSLANT_ITALIC))
		
		samurai_button= TextButton.new(@board,"Samurai",15)
		samurai_button.setFont(FXFont.new(app,"Times New Roman",24,FONTSLANT_ITALIC))
		
		woman_button= TextButton.new(@board,"Woman",14)
		woman_button.setFont(FXFont.new(app,"Times New Roman",25,FONTSLANT_ITALIC))
		
		river_button= TextButton.new(@board,"River",13)
		river_button.setFont(FXFont.new(app,"Times New Roman",25,FONTSLANT_ITALIC))
		
		person_button= TextButton.new(@board,"Person",12)
		person_button.setFont(FXFont.new(app,"Times New Roman",25,FONTSLANT_ITALIC))
		
		love_button= TextButton.new(@board,"Love",11)
		love_button.setFont(FXFont.new(app,"Times New Roman",25,FONTSLANT_ITALIC))
		
		light_button= TextButton.new(@board,"Light",10)
		light_button.setFont(FXFont.new(app,"Times New Roman",25,FONTSLANT_ITALIC))
		
		life_button= TextButton.new(@board,"Life",9)
		life_button.setFont(FXFont.new(app,"Times New Roman",25,FONTSLANT_ITALIC))
		
		man_button= TextButton.new(@board,"Man",8)
		man_button.setFont(FXFont.new(app,"Times New Roman",25,FONTSLANT_ITALIC))
		
		ice_button= TextButton.new(@board,"Ice",7)
		ice_button.setFont(FXFont.new(app,"Times New Roman",25,FONTSLANT_ITALIC))
		
		heart_button= TextButton.new(@board,"Heart",6)
		heart_button.setFont(FXFont.new(app,"Times New Roman",25,FONTSLANT_ITALIC))
		
		flower_button= TextButton.new(@board,"Flower",5)
		flower_button.setFont(FXFont.new(app,"Times New Roman",25,FONTSLANT_ITALIC))
		
		fire_button= TextButton.new(@board,"Fire",4)
		fire_button.setFont(FXFont.new(app,"Times New Roman",25,FONTSLANT_ITALIC))
		
		earth_button= TextButton.new(@board,"Earth",3)
		earth_button.setFont(FXFont.new(app,"Times New Roman",25,FONTSLANT_ITALIC))
		
		death_button= TextButton.new(@board,"Death",2)
		death_button.setFont(FXFont.new(app,"Times New Roman",25,FONTSLANT_ITALIC))
		
		dog_button= TextButton.new(@board,"Dog",1)
		dog_button.setFont(FXFont.new(app,"Times New Roman",25,FONTSLANT_ITALIC))

		def clickButton(button)
			@array<<button
			
		
		#When a button is clicked, wait for another button to be clicked and turn over the button which means changing its icon or text from nil to image_object
		#after two buttons have been clicked, access their @id values and compare them
		#if the @id values match, then it's a success - turn the backColor attribute of the buttons yellow or maybe there is a way to highlight their border so as not to cover the image up
		#if the @id values don't match, then flip the buttons back over - in other words, set their icons or text to nil
	

		
		
	end	
	
	def addClick
		@clickNumber+=1
		puts @clickNumber
	end
	
	
	def checkClick
		if @clickNumber==2 and @buttonArray[0].id==@buttonArray[1].id
		#clear buttonArray as the last step in this method so there are no buttons in it when @clickNumber resets to 0
			
			puts "you have a match"	
			
			
			@buttonArray=[]
			@clickNumber=0
			
		elsif @clickNumber==2
			
			app.addTimeout(2000)	do
					@buttonArray.each do |x|
						x.icon=nil
						x.text=nil
					end
				
				@buttonArray=[]
				@clickNumber=0
				
			

			end
		end

	end
	
	def pushButtonArray(button)
		@buttonArray<<button
		puts @buttonArray.inspect
	end
	
		
	def create
		super
		self.show(PLACEMENT_SCREEN)
	end

	



class PictureButton < FXButton
	def initialize(p,text,image_object,id)
		super(p,text,nil,:opts=>LAYOUT_EXPLICIT|FRAME_RAISED|BUTTON_NORMAL, :width=>100,:height=>100)
		@id=id
		@picObject = image_object
		@state=0
		
		
		self.connect(SEL_COMMAND) do |sender, sel, event|
			@picObject.create
			self.icon=@picObject
			parent.parent.addClick
			parent.parent.pushButtonArray(self)
			@state=1
			parent.parent.checkClick
			
		end
		 
	end
	
	def id
		@id
	end

	
	




class TextButton < FXButton
	def initialize(p,text,id)
		super(p,nil,:opts=>LAYOUT_EXPLICIT|FRAME_RAISED|BUTTON_NORMAL, :width=>100,:height=>100)
		@id=id
		@text = text
		@state=0
		
		self.connect(SEL_COMMAND) do |sender, sel, event|
			self.text=@text
			parent.parent.addClick
			parent.parent.pushButtonArray(self)
			@state=1
			parent.parent.checkClick
			
		end
	end
	
	def id
		@id
	end
	

	
end	
end
end

#horizontal frame 
 #on top is the frame and matrix
 #below is the textbox to add the time and number of boxes hit


app = FXApp.new
MemoryGameWindow.new(app)
app.create
app.run

---

### Post by Zill on 2013-01-17
makoshi563:  This looks like a general homework assignment rather than a specific Ubuntu question.  Please see the [Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy") Section II Para 7.
> While we are happy to serve as a resource for hints and for asking questions when you get stuck and need a little help, the Ubuntu Forums is not a homework service. Please do not post your homework assignments expecting someone else to do it for you. Any such threads will be taken offline and warnings or infractions may be issued.

---

