# whatsmeow
[![Go Reference](https://pkg.go.dev/badge/github.com/pbribeiro/whatsmeow-mysql.svg)](https://pkg.go.dev/github.com/pbribeiro/whatsmeow-mysql)

whatsmeow is a Go library for the WhatsApp web multidevice API.

## Discussion
Matrix room: [#whatsmeow:maunium.net](https://matrix.to/#/#whatsmeow:maunium.net)

For questions about the WhatsApp protocol (like how to send a specific type of
message), you can also use the [WhatsApp protocol Q&A] section on GitHub
discussions.

[WhatsApp protocol Q&A]: https://github.com/tulir/whatsmeow/discussions/categories/whatsapp-protocol-q-a

## Usage
The [godoc](https://pkg.go.dev/github.com/pbribeiro/whatsmeow-mysql) includes docs for all methods and event types.
There's also a [simple example](https://pkg.go.dev/github.com/pbribeiro/whatsmeow-mysql#example-package) at the top.

## Database Support
The library supports multiple database backends for storing WhatsApp session data:

* MySQL (recommended for production use)
* PostgreSQL
* SQLite (good for development and testing)

To use MySQL, you need to:

1. Install the MySQL driver:
```bash
go get github.com/go-sql-driver/mysql
```

2. Initialize the database connection:
```go
container, err := sqlstore.New("mysql", "user:password@tcp(localhost:3306)/dbname", nil)
if err != nil {
    panic(err)
}
```

The MySQL connection string format is:
```
user:password@tcp(host:port)/dbname?param=value
```

## Features
Most core features are already present:

* Sending messages to private chats and groups (both text and media)
* Receiving all messages
* Managing groups and receiving group change events
* Joining via invite messages, using and creating invite links
* Sending and receiving typing notifications
* Sending and receiving delivery and read receipts
* Reading and writing app state (contact list, chat pin/mute status, etc)
* Sending and handling retry receipts if message decryption fails
* Sending status messages (experimental, may not work for large contact lists)

Things that are not yet implemented:

* Sending broadcast list messages (this is not supported on WhatsApp web either)
* Calls
