---
title: "Docker"
date: 2018-12-06
forum: Programming Talk
---

### Post by stardawg on 2018-12-06
I have got a django web app running locally using nginx, postgres, gunicorn. I am using pipenv and fish shell. I am currently reading tutorials to find out how to write Dockerfile(s) and docker-compose to set all this up locally before I try with AWS.

I found a Linux Mint 17.3 docker image on docker hub but I know this comes with python 2.7. So say I wanted to start a project using python 3.6.6 I would just create a virtualenvironment using pipenv but as I understand I don't need to create a virtualenv in Docker as I can just specify everything in the image so that all my dependencies run globally inside the container. So my question is how do i integrate all this together : 

Firstly : Using python 3.6.6 as the default python in Linux Mint 17.3. I understand each Dockerfile should only have one From statement, So i guess I would use the Mint image and a separate python 3.6.6 image and combine them using docker-compose file? 
Then do i  specify pipenv in the Linux mint image or the python 3.6.6 image? 

And then how do i separate everything else? Does gunicorn and nginx go in separate containers or what??? I feel I will probably have some problems using fish instead of bash but I have found some resources and I am not too fussed about that at the moment.

I have just started learning Docker, I was just going to go the simple digital ocean way or just deploy to EC2 but Docker seems to be in demand now and I really want to learn it..


Thank you for any help. Cheers! :)

---

