# Telemetry-over-serial

Allows arduino sensor data to be sent over a serial device with some TCP-like features to ensure reliable transmission.
The interpretation program is written in python, each implementation can be found in their respective folders. 


Currently packets are arranged to have a header, payload and footer. Header contains data type and packet number and footer contains a checksum of the payload. 


Python packet interpreter checks validity of packets by keeping track of packet number, by checking packet begins with correct characters and checksum.

The main.py and arduino.ino are example usages - serial_handle.py and tcp.cpp include classes which are to integrate seem-lessly with other projects making telemetry as easy as possible


### Current work:

- [ ] implement checksum arduino functionality and validity check

- [ ] implement different packet types to allow for unchecked and checked packets (TCP/UDP)

- [ ] implement structure for sending commands to arduino

- [ ] allow dynamic packet sizes

- [ ] have some kind of packet identity so packets for different purposes can be requested - kind of like internet ports


### Issues:

<O_o>


#### Notes:

Data requester decides if packets are error checked - during handshake

Serial Handler
    Queues packets 
    Routes packets

Can different types of packets - each requires a handshake

Kw argument to decide if packet header/footer returned 

Handshake decides who is sending 

Beginning byte decides if conformation or not. 



###packet design - 

pre-header>
whether last packet was received correctly (0 if no error checking);
packets left in round;
// if packets to follow;
// handshake or not; (within datatype)
// if this is a full packet; (can be determined by length)

header>
//error checking; (associated with ID)
id;
data type;
packet number;

payload>
message;

footer>
checksum;
