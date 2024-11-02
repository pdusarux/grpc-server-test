# gRPC Server Test

A simple gRPC server implementation in Go that provides a greeting service.

## Description

This project implements a basic gRPC server that exposes a `SayHello` RPC endpoint. When called, it responds with a greeting message containing the name provided in the request.

## Prerequisites

- Go 1.23.2 or later
- Protocol Buffers compiler (protoc)
- Go plugins for Protocol Buffers

## Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/pdusarux/grpc-server-test.git
   cd grpc-server-test
   ```

2. Install the required dependencies:
   ```bash
   go mod tidy
   ```

## Working with Protocol Buffers

### Creating a .proto file

1. Create a new file with `.proto` extension (e.g., `proto/helloworld.proto`).
2. Define your protocol buffer schema:

   ```proto
   syntax = "proto3";

   option go_package = "grpc-server-test/proto";

   service Greeter {
       rpc SayHello(HelloRequest) returns (HelloResponse) {}
   }

   message HelloRequest {
       string name = 1;
   }

   message HelloResponse {
       string message = 1;
   }
   ```

### Generating Go Code from .proto File

To generate the Go code from your `.proto` file, run the following command:

```bash
protoc --go_out=. --go-grpc_out=. proto/helloworld.proto
```

## Running the Server

To run the gRPC server, execute the following command:

```bash
go run main.go
```

## Using Postman with gRPC

To test the gRPC server using Postman, follow these steps:

1. **Open Postman** and create a new request.
2. **Select the request type** as `gRPC`.
3. **Enter the URL** for your gRPC server, e.g., `localhost:50051`.
4. **Set the service definition**:
   - Choose `helloworld.proto` and select `Greeter/SayHello` as the method.
   - Use the following JSON structure for the `SayHello` method in Message field:
     ```json
     {
       "name": "YourName"
     }
     ```

## Credits

This project was created by [mikelopster](https://www.youtube.com/@mikelopster). Special thanks to mikelopster for the guidance in building a gRPC server.

- YouTube Channel: [mikelopster](https://www.youtube.com/@mikelopster)
- Video: [gRPC Server in Go](https://www.youtube.com/watch?v=YcwvN6utKvk)
