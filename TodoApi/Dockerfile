FROM mcr.microsoft.com/dotnet/sdk:latest as build-env
WORKDIR /app

COPY *.csproj ./
RUN dotnet restore

COPY . ./
RUN dotnet publish -c Release -o out

FROM mcr.microsoft.com/dotnet/aspnet
WORKDIR /app
#EXPOSE 80
COPY --from=build-env /app/out .
#ENTRYPOINT ["dotnet","TodoApi.dll"]
CMD ASPNETCORE_URLS=http://*:$PORT dotnet TodoApi.dll
