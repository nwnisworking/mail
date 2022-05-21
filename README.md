# mail

class Mailer{
	public $conn;
	public array $smtp;
	public function __construct()
	{
		$this->conn = stream_socket_client('tcp://localhost:25');
	}


}
$a = new Mailer();
// mail('admin@localhost', 'subject', 'message', "From: nwn@localhost\r\n");

$conn = stream_socket_client('tcp://localhost:25');
fwrite($conn, "HELO localhost:25"."\r\n");
var_dump(fread($conn, 1024));
ftruncate($conn, 1024);
fwrite($conn, "MAIL FROM:<nwn@localhost>\r\n");
ftruncate($conn, 1024);
fwrite($conn, "RCPT TO:<admin@localhost>\r\n");
fwrite($conn, "DATA\r\n");
fwrite($conn, "Date:");
fwrite($conn, "reorj\r\n.\r\n");
fwrite($conn, "QUIT\r\n");
