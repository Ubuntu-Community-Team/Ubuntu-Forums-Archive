---
title: "Fortran problem run-time error M6101 : MATH"
date: 2015-12-19
forum: Programming Talk
---

### Post by lam6 on 2015-12-19
Hi,guys 
i have a problem with a subroutine when i put D(i) = 1 i get ERROR M6101
but when D(i) = 0 the program run without problems  but all the results are wrong
[ATTACH=CONFIG]266248[/ATTACH]
this is what i write 

	real cord(20),Kg(20,20),IE(20),U(20),Ke(4,4),F(20),x1,x2
	+,long,R(20)
	integer nel,nn,nods(20,2),nd1,nd2,ipos(4),sdof
10    format(100E14.4e2)
	open(5,file='don')
	open(6,file='res')


	write(*,*)'nel='
	read(5,*) nel
	write(*,*) nel
	nn=nel+1
	sdof=nn*2


	write(*,*)'Les cordoonnées'
	read(5,*)(cord(i),i=1,nn)
	do 1 i=1,nn
		write(*,*)cord(i)
1	enddo


	write(*,*)'La matrice nods'
	read(5,*)((nods(i,j),j=1,2),i=1,nel)
	do 2 i=1,nel
		write(*,*)(nods(i,j),j=1,2)
2	enddo


	write(*,*)'les inertie IE'
	read(5,*)(IE(i),i=1,nel)
	write(*,*) (IE(i),i=1,nel)


	write(*,*)'Les forces exterieur'
	read(5,*)(F(i),i=1,sdof)
	write(*,*)(F(i),i=1,sdof)




	! initialisation des Ke et Kg et U


	do 50 i=1,sdof
	U(i)=1
50	enddo
	do 3 i=1,4
	do 3 j=1,4
	Ke(i,j)=0
3	enddo


	do 4 i=1,sdof
	do 4 j=1,sdof
	Kg(i,j)=0
4	enddo


	!Formation de Ke et Kg


	do 5 iel=1,nel
	nd1=nods(iel,1)
	nd2=nods(iel,2)
	x1=cord(nd1)
  	x2=cord(nd2)
	long=(x2-x1)
	write(*,*)'long='
	write(*,*) long
	write(*,*)'La matrice Ke',iel,'='
	call formK(Ke,long,IE,iel)
	do 6 i=1,4
	write(*,*)(Ke(i,j),j=1,4)
6	enddo
	ipos(1)=nd1*2-1
	ipos(2)=nd1*2
	ipos(3)=nd2*2-1
	ipos(4)=nd2*2
	write(*,*)'Le vecteur d indice ',iel,'='
	write(*,*)(ipos(i),i=1,4)
	do 7 i=1,4
	ii=ipos(i)
	do 7 j=1,4
	jj=ipos(j)
7	Kg(ii,jj)=Kg(ii,jj)+Ke(i,j)
5	enddo
	write(*,*)'La matrice Global='
	do 8 ii=1,sdof
	write(*,*)(Kg(ii,jj),jj=1,sdof)
8	enddo
	call solve_sys(U,R,Kg,F,sdof)
	do 21 i=1,nel
	call formK(Ke,long,IE,iel)					 
	do 21 ii=1,4								 
	F(i)=0
	do 21 jj=1,4
	F(ii)=F(ii)+ke(ii,jj)*U(jj)
21	continue
	write(*,*)'me deplacement U'
	write(*,*) (U(i),i=1,8)
	write(*,*)'les reaction'
	write(*,*)(R(i),i=1,8)
	end
	subroutine formK (Ke,long,IE,iel)
 	real Ke(4,4),IE(3),long
	integer iel
	ke(1,1)=12
	ke(1,2)=6*long
	ke(1,3)=-12
	ke(1,4)=6*long


	ke(2,1)=ke(1,2)
	ke(3,1)=ke(1,3)
	ke(4,1)=ke(1,4)


	ke(2,2)=4*long**2
	ke(2,3)=-6*long
	ke(2,4)=2*long**2


	ke(3,2)=ke(2,3)
	ke(4,2)=ke(2,4)
	
	ke(3,3)=12
	ke(3,4)=-6*long


	ke(4,3)=ke(3,4)


	ke(4,4)=4*long**2


	do 9 i=1,4
		do 9 j=1,4
			ke(i,j)=ke(i,j)*IE(iel)/(long**3)
9	enddo
	end	subroutine formK
	subroutine solve_sys(D,reac,Kg,F,n)
	parameter (ID=20)
	real Kg(ID,ID),F(ID),reac(ID),At,som,A(ID,ID),X(ID),b(ID,2)
	+,U(ID),D(ID)
	integer n,nm 
	im=0
	do 10 i=1,n
	if(D(i).NE.0)then
	im=im+1
	b(im,1)=F(i)
	b(im,2)=i
	jm=0
	do 11 j=1,n
	jm=jm+1
	A(im,jm)=Kg(i,j)
11	enddo
	endif
10	enddo
	nm=im
	do 12 k=1,nm-1
	do 13 i=k+1,nm
	if(abs(A(i,k)).GT.abs(A(k,k)))then
	do 14 j=k,nm
	call exchange(A(i,j),A(k,j))
14	enddo
	call exchange(b(k,1),b(i,1))
	endif
13	enddo
	do 15 i=k+1,nm
	At=A(i,k)
	do 16 j=k,nm
	A(i,j)=A(i,j)-A(k,j)/A(k,k)*At
16	enddo
	b(i,1)=b(i,1)-b(k,1)/A(k,k)*At
15	enddo
12	enddo
	do 17 i=nm,1,-1
	som=0
	do 18 j=i+1,nm
	som=som+A(i,j)*X(j)
18	enddo
	X(i)=(b(i,1)-som)/A(i,i)
	U(b(i,2))=X(i)
17	enddo
	do 19 i=1,n
	if(D(i).EQ.0)then
	reac(i)=-F(i)
	do 20 j=1,n
	reac(i)=reac(i)+A(i,j)*D(j)
20	enddo
	endif
19	enddo
	return
	end subroutine solve_sys
	subroutine exchange(A,B)
	real A,B
	A=A+B
	B=A-B
	A=A-B
	return
	end subroutine exchange

---

