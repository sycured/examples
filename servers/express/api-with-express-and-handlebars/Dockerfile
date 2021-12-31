FROM node:lts-bullseye-slim as base
ENV NODE_ENV production
USER node
WORKDIR /home/node

FROM base AS deps
COPY package.json package-lock.json ./
RUN npm ci

FROM base as final
EXPOSE 3000
COPY --from=deps /home/node/node_modules ./node_modules
COPY . .
CMD ["npm", "start"]
