FROM golang:1.13.5-alpine3.10
WORKDIR /build
COPY . .
#RUN apk --no-cache add build-base
RUN GOOS=linux CGO_ENABLED=0 go build -a -ldflags '-s -w -extldflags "-static"' -o app .

FROM alpine:3.10
RUN apk --no-cache add ca-certificates
WORKDIR /app
COPY --from=0 /build/app .
CMD ["./app"]