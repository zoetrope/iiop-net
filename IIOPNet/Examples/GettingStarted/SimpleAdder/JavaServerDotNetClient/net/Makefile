include ..\..\..\..\..\MakeVars

IDLSource=..\java\IDL\ch\elca\iiop\tutorial\gettingstarted\*.idl 
Adder=ch\elca\iiop\tutorial\gettingstarted\ 
IDLToCLS=..\..\..\..\..\..\IDLToCLSCompiler\IDLCompiler\bin\IDLToCLSCompiler.exe
TARGETASM=adder
IIOPCHANNEL = ..\..\..\..\..\IIOPChannel\bin\IIOPChannel.dll
BIN=bin\ 
IDL=IDL\ 

build: build-idl build-client

$(BIN)IIOPChannel.dll: $(IIOPCHANNEL)
	copy /y $(IIOPCHANNEL) $(BIN)IIOPChannel.dll

$(BIN) $(IDL):
	if not exist $@nul mkdir $@

build-idl: $(IDL)
	copy ..\..\..\..\..\IDLToCLSCompiler\IDL\*.idl $(IDL)
	xcopy /s /y ..\java\IDL $(IDL)
	cd $(IDL)
	$(IDLToCLS) -o ..\$(BIN) $(TARGETASM) $(Adder)Adder.idl
	cd ..

build-client: $(BIN)$(TARGETASM).dll $(BIN)IIOPChannel.dll NClient.cs
	$(CSC) /r:$(BIN)$(TARGETASM).dll /r:$(BIN)IIOPChannel.dll /out:$(BIN)NClient.exe NClient.cs

clean:
	if exist $(IDL)nul rmdir /q /s $(IDL)
	if exist $(BIN)nul rmdir /q /s $(BIN)

