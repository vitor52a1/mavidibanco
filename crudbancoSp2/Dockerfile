FROM maven:3.8.5-openjdk-11-slim AS builder
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

FROM openjdk:11-jre-slim
WORKDIR /app
COPY --from=builder /app/target/*.jar app.jar

RUN useradd -m appuser
USER appuser

ENTRYPOINT ["java", "-jar", "app.jar"]
