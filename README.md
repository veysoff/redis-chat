# redis-chat

chat app with ASP.NET Core, SignalR and Redis. This example uses the pub/sub feature combined with Websockets from SignalR for implementing the message communication between client and server.

## Technical Stack
Frontend - React, Socket (@microsoft/signalr)
Backend - .Net, Redis (Microsoft.Extensions.Caching.StackExchangeRedis)

### Database Schema

#### User

```csharp
public class User : BaseEntity
{
  public int Id { get; set; }
  public string Username { get; set; }
  public bool Online { get; set; } = false;
}
```

#### ChatRoom

```csharp
public class ChatRoom : BaseEntity
{
  public string Id { get; set; }
  public IEnumerable<string> Names { get; set; }
}
```

#### ChatRoomMessage

```csharp
public class ChatRoomMessage : BaseEntity
{
  public string From { get; set; }
  public int Date { get; set; }
  public string Message { get; set; }
  public string RoomId { get; set; }
}
```

## How to run it locally?

#### Write in environment variable or Dockerfile actual connection to Redis:

```
   REDIS_ENDPOINT_URL = "Redis server URI:PORT_NUMBER"
   REDIS_PASSWORD = "Password to the server"
```

#### Run backend

Build the Redis container with the following command:
```sh
  docker-compose up -d
```

From the _BasicRedisChat_ Directory execute:

```sh
dotnet run
```
