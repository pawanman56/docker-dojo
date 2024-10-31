# Stage 1
FROM --platform=linux/x86_64 gradle:6.0.1-jdk8 AS builder
WORKDIR /app
COPY . .
RUN gradle installDist

# Stage 2
FROM openjdk:8-jre-alpine
WORKDIR /app
COPY --from=builder /app/build/install/charts/ .
ENTRYPOINT ["./bin/charts"]
