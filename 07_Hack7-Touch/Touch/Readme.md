## Touch.v
Touch controls transmission to Touch-Screen controller according to timing diagramm of SPI (serial peripherial interface).

* If (load == 1) & (run == 0) Touch starts serial transmission of 8 bits in[7:0].

* During transmission out = -1 (16 bit)
* At end of transmission out = received byte (8 bit)

### Proposed implementation (draft)

* Use a Switch to store run state
* if (load==1) and (run == 0) start = 1
* bits[16:3] count the received/transmitted bits (trigger when bits[2:0]==3'b111)
* Use a ShifterL to store transmitted/received byte.

![](Touch.png)

## Touch_tb.v
Testbench starts transmission of a 8 bit data (load=1). Received byte should be inverse of transmitted byte (mosi is inverted to miso).

![](Touch_tb.png)
## Project
* Implement `Touch.v`
* Test with testbench `Touch_tb.v`  
`$ apio sim`
* Compare timing diagram with `Touch_tb.png`
