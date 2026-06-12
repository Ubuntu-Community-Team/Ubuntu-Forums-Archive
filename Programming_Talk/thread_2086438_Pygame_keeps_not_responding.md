---
title: "Pygame keeps not responding"
date: 2012-11-20
forum: Programming Talk
---

### Post by EnexOD on 2012-11-20
I am trying to create a battleship in pygame and it works okay but after a bit the pygame screen doesn't respond but the console is still running.

*I'm pretty sure the problem is in the for loop in method ask() but I'm not completely sure*
*Also, I have the user enter information on the cmd window, not the actual pygame window*
Here is the code: 

```
import pygame, os, time, sys, string, random
ran=random.randint(0,9)
ran1=random.randint(0,9)
running=0
count=0
game=True
#stats
shots=0
hits=0
pygame.init()
pygame.display.set_caption("kBattleship")
#size
size=(640,480)
screen=pygame.display.set_mode(size)

#colours
white=(255,255,255)
black=(0,0,0)
red=(255,0,0)
green=(0,200,0)
grey=(51,51,51)

#images
ship=pygame.image.load(os.path.join("ship.png"))
grid=pygame.image.load(os.path.join("grid.png"))
dot=pygame.image.load(os.path.join("dot.png"))

pygame.display.flip()
myGrid=[["~","~","~","~","~","~","~","~","~","~"],
		["~","~","~","~","~","~","~","~","~","~"],
		["~","~","~","~","~","~","~","~","~","~"],
		["~","~","~","~","~","~","~","~","~","~"],
		["~","~","~","~","~","~","~","~","~","~"],
		["~","~","~","~","~","~","~","~","~","~"],
		["~","~","~","~","~","~","~","~","~","~"],
		["~","~","~","~","~","~","~","~","~","~"],
		["~","~","~","~","~","~","~","~","~","~"],
		["~","~","~","~","~","~","~","~","~","~"]]

compGrid=[["~","~","~","~","~","~","~","~","~","~"],
		  ["~","~","~","~","~","~","~","~","~","~"],
		  ["~","~","~","~","~","~","~","~","~","~"],
		  ["~","~","~","~","~","~","~","~","~","~"],
		  ["~","~","~","~","~","~","~","~","~","~"],
		  ["~","~","~","~","~","~","~","~","~","~"],
		  ["~","~","~","~","~","~","~","~","~","~"],
		  ["~","~","~","~","~","~","~","~","~","~"],
		  ["~","~","~","~","~","~","~","~","~","~"],
		  ["~","~","~","~","~","~","~","~","~","~"]]

fourfour=[["~","~","~","~","~","~","~","~","~","~"],
		  ["~","~","~","~","~","~","~","~","~","~"],
		  ["~","~","~","~","~","~","~","~","~","~"],
		  ["~","~","~","~","~","~","~","~","~","~"],
		  ["~","~","~","~","~","~","~","~","~","~"],
		  ["~","~","~","~","~","~","~","~","~","~"],
		  ["~","~","~","~","~","~","~","~","~","~"],
		  ["~","~","~","~","~","~","~","~","~","~"],
		  ["~","~","~","~","~","~","~","~","~","~"],
		  ["~","~","~","~","~","~","~","~","~","~"]]

def showship(): #nested for loop for user's grid
	for row in range(0,10):
		for col in range(0,10):
			print myGrid[row][col],
		print ""
def showship2(): #nested for loop for comp's grid
	for row in range(0,10):
		for col in range(0,10):
			print compGrid[row][col],
		print ""
def decoy(): #nested for loop for the decoy gird
	for row in range(0,10):
		for col in range(0,10):
			print fourfour[row][col],
		print ""	
def ask(): #asks the user to input the location of the ships
	for d in range(0,5):
		os.system("CLS")
		print ""
		print "Battleship #",d+1
		print "-----------------"
		r=input("Row (0-9): ")
		c=input("Column (0-9): ")
		screen.blit(dot,(int(23.5*r),int(23.6*c)))
		if myGrid[r-1][c-1]=="@":
			print "You already have a ship at that location"
			print ""
			r=input("Row (0-9): ")
			c=input("Column (0-9): ")
		else:
			myGrid[r-1][c-1]="@"
	pygame.display.flip()
def genrandom():
	for d in range(0,5):
		ran=random.randint(0,9)
		ran1=random.randint(0,9)
		if compGrid[ran][ran1]=="@":
			ran+=1
			ran+=1
			compGrid[ran][ran1]="@"
		else:	
			compGrid[ran][ran1]="@"
		print "ship#",d+1," - "+"x=",ran,"y=",ran1
		time.sleep(1)
#font
font=pygame.font.Font(None,64)
font2=pygame.font.Font(None,30)
title=font.render("Battleship",True,(white),grey)
play=font.render("[P]lay!",True,(white),grey)
list=font.render(str(myGrid),True,(white),grey)
screen.fill(black)
pygame.display.flip()
while (running!=-1):
	#menu
	while (running==0):
		event=pygame.event.poll()
		screen.fill(grey)
		screen.blit(title,(190,50))
		screen.blit(ship,(170,100))
		screen.blit(play,(250,430))
		#screen.blit(list,(0,0))
		if (event.type==pygame.QUIT):
			running=-2
		if (event.type==pygame.KEYDOWN):
			if (event.key==pygame.K_p):
				running=1
		pygame.display.flip()
		
	#once user has pressed p
	while (running==1):
		event=pygame.event.poll()
		screen.fill(grey)
		screen.blit(grid,(0,0))
		screen.blit(grid,(0,243))
		#screen.blit(dot,(260,260))
		#screen.blit(dot,(260,300))
		#screen.blit(dot,(260,340))
		#screen.blit(dot,(260,380))
		#screen.blit(dot,(260,420))
		x,y = pygame.mouse.get_pos()
		#pygame.display.flip()
		count=1
		if count==1:
			ask()
			count=2
		if count==2:
			genrandom()
			print ""
			print ""
			print "Your battlefield!"
			print "-------------------"
			mShip=5
			cShip=5
			while (game==True):
				#ran=random.randint(0,9)
				#ran1=random.randint(0,9)
				os.system("CLS")
				print ""
				print "----------------------"
				r1=input("Row (0-9): ")
				c1=input("Column (0-9): ")
				
				#Your Grid
				if compGrid[r1][c1]=="@":
					print ""
					print "You hit a ship!"
					compGrid[r1][c1]="#"
					fourfour[r1][c1]="#"
					cShip=cShip-1
					shots+=1
					hits+=1
					acc=round(float(hits)/shots*100,2)
					print "Shot(s)=",shots
					print "Hit(s)=",hits
					print "Acc=",acc,"%"
					time.sleep(1)
				elif compGrid[r1][c1]=="X" or compGrid[r1][c1]=="#":
					print "You already hit that location..."
					time.sleep(1)
				else:
					print ""
					print "You hit water!"
					print ""
					compGrid[r1][c1]="X"
					fourfour[r1][c1]="X"
					shots+=1
					acc=round(float(hits)/shots*100,2)
					print "=========="
					print "Shot(s)=",shots
					print "Hit(s)=",hits
					print "Acc(s)=",acc,"%"
					print "=========="
					time.sleep(1)

				#Computer's Grid
				if myGrid[ran][ran1]=="@":
					myGrid[ran][ran1]=="#"
					print "The Computer hit a ship!"
					mShip=mShip=1
					time.sleep(1)
				elif myGrid[ran][ran1]=="X" or myGrid[ran][ran1]=="#":
					ran=random.randint(0,9)
					ran1=random.randint(0,9)
					if myGrid[ran][ran1]=="X" or myGrid[ran][ran1]=="#":
						print "Computer is stupid"
					elif myGrid[ran][ran1]=="~":
						print "Computer Missed!"
					time.sleep(1)
				else:
					myGrid[ran][ran1]="X"
					print "The Computer Missed!"
					time.sleep(1)

				#if game is over
				if mShip==0:
					os.system("CLS")
					print "All your ships has been sunk!"
					time.sleep(1)
					print "The computer is victorious!"
					time.sleep(1)
					break
				elif cShip==0:
					os.system("CLS")
					print "The computer's ships has been sunk!"
					time.sleep(1)
					print "You are victorious!"
					time.sleep(1)
					break 
		pygame.display.flip()

		



pygame.quit()
sys.exit()

```

---

