---
title: "I need Help for convert bat in shell syntax PLEASE"
date: 2016-08-04
forum: New to Ubuntu
---

### Post by thiagoazeredo on 2016-08-04
@echo off

set logFile=%~d0%~p0LOG\%~n0_%date:~6,4%%date:~3,2%%date:~0,2%-%time:~0,2%%time:~3,2%%time:~6,2%.log
set logFile=%logFile: =%
set pubFile=%~d0%~p0CONFIGURACION\OD_FDC_2.pub
set outputPath=%~d0%~p0OUTPUT\
set inputPath=%~d0%~p0INPUT\
set imagePath=%~d0%~p0IMAGES\
set engineExe=%~d0%~p0\Engine\engine.9.5.102.x64.sb\ProdEngine.exe
set engineLicence=%~d0%~p0\Engine\license\INTELLID_V9_08-31-16_20150915.ekf
set msgResource=%~d0%~p0\Engine\engine.9.5.102.x64.sb\MsgResource_pt-br.dat
set javaExe=%~d0%~p0\dist\mapfreTarjetas.jar


call > print Inicio de el Proceso de Generacion

call :print Procesando archivos UWMS
for %%f in (%inputPath%UWMS_*.TXT) do (
    call :print generando: %%f
    call java -jar %javaExe% %%~nf.txt
    call %engineExe% -MSGRESOURCE=%msgResource% -RUNMODE=PRODUCTION -KEYFILE=%engineLicence% -PACKAGEFILE=%pubFile% -FILEMAP=DRIVER1,%%f -ALLOW_EMPTY_REF_FILES -MESSAGEFILE=%logFile%.tmp -VARSET=TipoInputFile,1 -VARSET=RutaImagenes,%imagePath% -OUTPUTDIRECTORY=%outputPath%UWMS\ -FILEMAP=REPORT,%outputPath%%%~nf_RETORNO.txt -FILEMAP=REPORTVV,%outputPath%%%~nf_RETORNO_VV.txt
    type %logFile%.tmp >> %logFile%
    del %logFile%.tmp
    call :print terminado: %%f

goto finProceso

rem funciones
:print
set fechaTmp=%date:~6,4%/%date:~3,2%/%date:~0,2%
set horaTmp=%time:~0,2%:%time:~3,2%:%time:~6,2%,%time:~9,4%
echo %fechaTmp% %horaTmp%    %*
echo %fechaTmp% %horaTmp%    %* >> %logFile%
goto:eof

:finProceso
call : print Fin de el Proceso de Generacion

---

### Post by howefield on 2016-08-04
Duplicate thread closed.

---

